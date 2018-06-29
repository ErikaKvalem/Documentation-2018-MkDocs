# 3. Tutorial cbcbeat

## 3.1 demo_monodomain.py

To run both The Beeler-Reuter model and FitzHugh-Nagumo model the demo_monodomain.py provided by cbcbeat was used. This code goes as expalined here:

**1**.	The first lines are comments describing what the demo is used for. 

**2**.	It imports **cbcbeat** and **Fenics **.

**3**.	Turns off the adjoint functionality.

**4**.	Defines the geometry.

This can be either 2D or 3D (higher computational cost). The mesh is based on rectilinear divisions and it could be fine or coarse depending on the specified values. In this case the mesh used is **UnitSquareMesh meaning** the side of the spatial domain is of length 1 and has 100 divisions.
```
mesh = UnitSquareMesh(100, 100)

time = Constant(0.0)
```

**5**.	Define the conductivity (tensors).

Assigns a value for the membrane’s ability to **conduct the electric current** at intracellular and extracellular level. 
```
M_i = 2.0
M_e = 1.0
```

**6**.	Choose the cell model.

Calls the specified **cell model**. In the file **supported_cell_models** the different tested models can be found.  In this example **FitzHughNagumoManual**
```
cell_model = FitzHughNagumoManual() 

```

**7**.	Define the stimulus.

In this line the  **initiating stimulus** is defined. The stimulus can be defined in many ways these are some examples: 

- demo_monodomain
 
```

Polynomial of degree 1: stimulus = Expression("10*t*x[0]", t=time, degree=1)
```

- demo_single_cell_model

```

cell = CardiacCellModel() cell.stimulus = Expression(“I_s(t)”, degree=1)
```


- demo_benchmark
```
    duration = 2. # ms
    A = 50000. # mu A/cm^3
    cm2mm = 10.
    factor = 1.0/(chi*C_m) # NB: cbcbeat convention
    amplitude = factor*A*(1./cm2mm)**3 # mV/ms
    I_s = Expression("time >= start ? (time <= (duration + start) ? amplitude : 0.0) : 0.0",
                      time=time,
                      start=0.0,
                      duration=duration,
                      amplitude=amplitude,
                      degree=0)
                    
                      
```

**9**.	**Save this configuration** into de CardiacModel.
```
cardiac_model = CardiacModel(mesh, time, M_i, M_e, cell_model, stimulus)
```

**10**.	**Choosing the  solver** that will be used further on to solve the problem. 

This will go through the equations and provide a solution field. In this case it uses the default parameters specified in the FitzHughNagumoManual file. 

```
ps = SplittingSolver.default_parameters()
ps["theta"] = 0.5                        # Second order splitting scheme
ps["pde_solver"] = "monodomain"          # Use Monodomain model for the PDEs
ps["CardiacODESolver"]["scheme"] = "RL1" # 1st order Rush-Larsen for the ODEs
ps["MonodomainSolver"]["linear_solver_type"] = "iterative"
ps["MonodomainSolver"]["algorithm"] = "cg"
ps["MonodomainSolver"]["preconditioner"] = "petsc_amg"

solver = SplittingSolver(cardiac_model, params=ps)
```


**11**.	**Solution field** and **initial conditions**. 

The solution obtained from the solver will be divided into the different variables giving as a result the solution field that is defined in the following way. Morover, the initial conditions are set up as the ones defined in initial_conditions in the **cell model**. 
```
(vs_, vs, vur) = solver.solution_fields()
vs_.assign(cell_model.initial_conditions())
```

**12**.	Setting up the **time step**. 

These are crucial lines in the code since the final solution will highly depend on the time interval and period. Very small-time step can lead to problems with instability and divergence. Very big-time step can lead to loss in accuracy. That is why this parameter should be chosen carefully depending on what it is being studied. 

```
dt = 0.1
T = 1.0
interval = (0.0, T)
```

**13**.	**Total time** it takes to solve the problem

```
timer = Timer("XXX Forward solve") # Time the total solve
```
* The following line is inserted just after the solving part (14) 
```
timer.stop() 

```

**14**.	**Solving the problem**.

It uses the solver, the time step specified, the solution field, the initial conditions. In this case it also prints how much memory is used in obtaining the result in case it is needed to compare it with another conditions. 

```

# Solve!
for (timestep, fields) in solver.solve(interval, dt):
    print "(t_0, t_1) = (%g, %g)", timestep

    # Extract the components of the field (vs_ at previous timestep,
    # current vs, current vur)
    (vs_, vs, vur) = fields

    # Print memory usage (just for the fun of it)
    print memory_usage()
```

**15**.	**Plot of the results**, in this case transmembrane potential. 

When using **Docker**, no plot is shown. However, visualization of the results is possible thanks to **Paraview.** 
```
# Visualize some results
plot (vs [0], title="Transmembrane potential (v) at end time")
      plot (vs [1], title="1st state variable (s_0) at end time")
      
```

**16**.	**ADDED EXTRA LINES for visualization in Paraview**. 

The name of the **folder** where the **.xdmf** file will be stored and name of the **file** are  defined. The second line specifies what **variable** should be included in the. xdmf file. This will create an .xdmf file that will be open in Paraview showing the plot. 
```
# Create XDMF files for visualization output
xdmffile_vs = XDMFFile('vs/TransmembranePotential.xdmf')

# Save solution to file (XDMF/HDF5)
xdmffile_vs.write(vs)
```

**17**.	**Final lines**.

It shows how much time was spent in the different process when computing the solution. This will allow to configure the time step to optimize the computing time and the solution. The **interactive()** line should be commented to avoid errors. 

```
# List times spent
list_timings(TimingClear_keep, [TimingType_user])

print "Success!"
interactive()

```


## 3.2 demo_single_cell_solverm.py

**1**.	The first lines are comments describing what the demo is used for. 

**2.** Author: Marie E. Rognes 2017
```

__author__ = "Marie E. Rognes (meg@simula.no), 2017"
```

**3**.	It imports **math**, **pylab** and **cbcbeat** 

```
import math
import pylab
from cbcbeat import *
```


**4**.	Turns off the adjoint functionality. Adjust for better visualization and faster computing (explanation out of scope)
```

# Disable adjointing
parameters["adjoint"]["stop_annotating"] = True

# For easier visualization of the variables
parameters["reorder_dofs_serial"] = False

# For computing faster
parameters["form_compiler"]["representation"] = "uflacs"
parameters["form_compiler"]["cpp_optimize"] = True
flags = "-O3 -ffast-math -march=native"
parameters["form_compiler"]["cpp_optimize_flags"] = flags
```


**5**.	Defines the stimulus.

In this case as a self-defined stimulus. When the variable time takes values between two limiting values (2 and 11 in this case) the stimulus has a specific amplitude and value (in this case v_amp=125 and value=0.05 * v_amp) otherwise value= 0.
```
class Stimulus(Expression):
    "Some self-defined stimulus."
    def __init__(self, **kwargs):
        self.t = kwargs["time"]
    def eval(self, value, x):
        if float(self.t) >= 2 and float(self.t) <= 11:
            v_amp = 125
            value[0] = 0.05*v_amp
        else:
            value[0] = 0.0
```

**6 .** Plot of the results against time. 

Frist it defines the function for plot introducing the time and the variable that will be plotted against it (in this case values). The zip() function take iterables (in this case values), makes iterator that aggregates elements based on the iterables passed, and returns an iterator of tuples. After that the dimensions of the plot are defined (20 by 10 in this case).
```

def plot_results(times, values, show=True):
    "Plot the evolution of each variable versus time."
    variables = zip(*values)
    pylab.figure(figsize=(20, 10))
    
```
Calculating the rows it will only be useful in case a subplot is needed. 
```

    rows = int(math.ceil(math.sqrt(len(variables))))
```
**7.** Next is a **For loop**

The loop is over the parameter variables (with an automatic counter) because it uses the  built-in Python function *enumerate*. Based on that, it creates a plot (var vs time) with specific type of **line**, **title**, **xlabel**, choses to activate or deactivate the **grid** and other adjustments.

```
 for (i, var) in enumerate([variables[0],]):
        #pylab.subplot(rows, rows, i+1)
        pylab.plot(times, var, '*-')
        pylab.title("Var. %d" % i)
        pylab.xlabel("t")
        pylab.grid(True)
```

**8.** This plot is saved as a pdf file in the following way:

```
 info_green("Saving plot to 'variables.pdf'")
    pylab.savefig("variables.pdf")
    if show:
        pylab.show()
```

**9.** Now it calls the main function. 

This is the most important part of the code. First the cell model is selected along with the parameters in this case default ones. If default is not chosen then the parameters are the ones written in this code. Moreover, also the stimulus is initialized here calling the function defined previously. 

```
def main(scenario="default"):
    "Solve a single cell model on some time frame."

    # Initialize model and assign stimulus
    params = Beler_reuter_1977.default_parameters()
    if scenario is not "default":
        new = {"g_Na": params["g_Na"]*0.38,
               "g_CaL": params["g_CaL"]*0.31,
               "g_Kr": params["g_Kr"]*0.30,
               "g_Ks": params["g_Ks"]*0.20}
        model = beeler_reuter_1977(params=new)
    else:
        model = beeler_reuter_1977()
        
    time = Constant(0.0)
    model.stimulus = Stimulus(time=time, degree=0)
```
  
Inside the main function the solver is initialized. In this case **SingleCellSolver** is the one being used along default parameters. The sovler needs as input the model, the time and the parameters. 

```
    # Initialize solver
    params = SingleCellSolver.default_parameters()
    params["scheme"] = "GRL1"
    solver = SingleCellSolver(model, time, params)
 ```
 
The solver fileds are defined (in this case vs_ and vs). For the solver to be able to extract the values initial conditions are needed. These are speficied in the cell model. Furthermore, the time step and the interval are defined. After that the solver is called. The for loop will append each solution to to times and values in this case and that is what it will be returned. 

 
