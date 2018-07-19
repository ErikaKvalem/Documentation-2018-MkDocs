# 5. CellML models in OpenCOR 
For a better understanding of the models **OpenCOR** is used in order to visualize the behaviour of the different key parameters of the model.

## 5.1 The Beeler Reuter model 

The following screenshot refers to the **Beeler Reuter model** run by OpenCOR. There are four plots regarding the different parameters.

The first one shows the **voltage dependence on time  V(t)**  also known as **action potential**. It can be distinguished the depolarization, plateau and repolarization phases of the action potentail of a **cardiac cell.** 

The second reffers to the **fast inward current (I<sub>Na</sub>)**. This one has a very brief downward (inward current) spike that is triggered when the membrane voltage reaches around **-70 mV**. This is caused by the big increase in sodium channel conductance (g<sub>Na</sub>(t)). This is related simultaneously with the **fourth plot**; the opening and closing of the **m** and **h** gates. 

The third plot shows the time dependent outward current I<sub>K1</sub> and the time independent outward current  I<sub>x1</sub>. 

The fourth plot gathers both the **m gate and the h gate**. The opening of m gate coincides with the spike from the  **fast inward current (I<sub>Na</sub>)** seen in the second graph. The m gate is open during the plateau and is closed when the h gate opens. 

The last plot refers to the **second slower inactivation gate j**. This is a special characteristic of this model since the Hodgkin and Huxley does not include this variable.  The total ionic current in the Beeler-Reuter model is given by **four currents**, and the model uses **eight variables**.

![beelerreuter2](https://user-images.githubusercontent.com/39902241/42158670-68bdde56-7df1-11e8-9662-d92f4916b663.jpg)

## 5.2 The Fitzhugh Nagumo model 

The following screenshot refers to the **Fitzhugh Nagumo model**  run by OpenCOR. There are two plots regarding the different parameters. 

In this case, since this model is an **Empirical model** which aims for a larger spatial and temporal scale only the **V(t) voltage dependence on time** and the **W(t) recovery variable** are plotted. 

The first plot shows the **Voltage dependence with time V(t)**. Comparing it with the second plot **(recovery variable W(t))** it can be seen that **depolarization** occurs when the recovery variable is at its **minimum**.When the **plateau** is happening the recovery variable increases until **repolarisation**. It reaches the highest value just before  going into this phase. 

This helps the **V(t)** to recover in a **progressive** way until the threshold voltage is achieved again and a new Action potential is triggered. 

![fitzhughnagumo1](https://user-images.githubusercontent.com/39902241/42159608-ae84695c-7df4-11e8-91f9-6da7f53e6f98.jpg) 

Paraview visualization: 

<a href="https://imgflip.com/gif/2dnqo8"><img src="https://i.imgflip.com/2dnqo8.gif" title="made at imgflip.com"/></a>

## 5.3 The ten Tusscher, Panfilov, 2006 model 

This model is slightly more complex than the ones previously mentioned. It uses 12 transmembrane currents listed here: 

- Fast **Na<sup>+</sup>** current 

- L-type **Ca<sup>+2</sup>** current 

- Rapid  delayed rectifier **K<sup>+</sup>** current

- Slow delayed rectifier **K<sup>+</sup>** current

- Inward rectifier **K<sup>+</sup>** current

- Transient outward **K<sup>+</sup>**

- Plateau **K<sup>+</sup>** current 

- **Na<sup>+</sup>-Ca<sup>+2</sup>** exchanger current

- **Na<sup>+</sup>-K<sup>+</sup>** pump current

- Sarcolemmal **Ca<sup>+2</sup>** pump current

- Background **Na<sup>+</sup>** current

- Background **Ca<sup>+2</sup>** current.

From those currents some have been represented in the screenshot below (The action potential, **K<sup>+</sup>** current, L-type  **Ca<sup>+2</sup>** current , background **Na<sup>+</sup>** current and **Na<sup>+</sup>-K<sup>+</sup>** pump current).

The interpretation and relation of the graphs is out of the scope of this page. However it is relevant to get an idea on how complex and complete this models can get, trying to simulate reality as much as they can.


![tentussher](https://user-images.githubusercontent.com/39902241/42164153-610cf7fa-7e05-11e8-8f0b-6976fc2bbd2b.jpg)

## 5.4 Nygren 1998 cell  model 

 The following screenshot refers to the **Nygren 1998 cell  model **  run by OpenCOR.
 
 The graphs refer to the **ionic current** waveforms during **AP**. I<sub>Na</sub>  is the first to respond to depolarizing stimulus pulse (delivered at time=0.1).  I<sub>Na</sub>  activates rapidly and therefore there is a large **transient inward current**. This will generate the upstroke in the initial phase of the AP. 
 
 In the depolarizing phase I<sub>t</sub>, I<sub>sus</sub> and I<sub>CaL</sub> are also activated. I<sub>t</sub>, I<sub>sus</sub> reach their peak faster than  I<sub>CaL</sub> resulting in a bigger magnitude. This leads to rapid repolarization dominated by I<sub>t</sub>. Since time of inactivation is bigger for I<sub>CaL</sub> the net current is gradually dominated by it. 
 
 At the plateau phase of the AP there is a balance between I<sub>sus</sub> (and remaining  I<sub>t</sub>) repolarizing and I<sub>CaL</sub> depolarizing. 
 
 When I<sub>CaL</sub> inactivates, I<sub>sus</sub> dominates and togheter with rectifier currents (I<sub>K1</sub>,I<sub>K,r</sub>, I<sub>K,s</sub>)the cell AP goes back to **resting potential**.


![screen shot 2018-07-11 at 11 12 48 am](https://user-images.githubusercontent.com/39902241/42563196-eaf838ae-84fd-11e8-8aef-96dd5ad7ff9f.jpg)


## 5.5 Courtemanche 1998 cell model

Behavior of the model action potential. In the image it can be seen the control model action potential from the Courtemanche model. This model shows a spike-and-dome shape. 

The action potential is initiated by the **I<sub>Na</sub>** **(Phase 0)**. 

After that,  repolarization produced by the transient outward current **(I<sub>to</sub>)** follows **(phase 1)**.

Rapid  **Ca<sup>+2</sup>** dependent inactivation is the next process **(phase 2)**. 

After that **I<sub>to</sub>** and **I<sub>CaL</sub>** inactivation occurs, causing slight depolarization of the membrane. This is the main cause of the **dome morphology** **(phase 3)**. 

Due to this, there is a net inward current that is countered by slowly activating outward **I<sub>k</sub>** leading to slow repolarization. **(phase 4)**

The final phase is slow late repolarization caused by a balance between deactivating **I<sub>k</sub>**  and time independent **I<sub>k1</sub>** together with opposing inward current generated by the **Na<sup>+</sup>/Ca<sup>+2</sup>** exchanger. **(phase 5)**

![output_7g9fk5](https://user-images.githubusercontent.com/39902241/42940010-323c7472-8b58-11e8-9b7e-db3a19bf923c.gif)


## 5.6 Maleckar 2009 cell model












