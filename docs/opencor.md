# 4. CellML models in OpenCOR 
For a better understanding of the models OpenCOR is used in order to visualize the behaviour of the different key parameters of the model.

## The Beeler Reuter model 

The following screenshot refers to the Beeler Reuter model run by OpenCOR. There are four plots regarding the different parameters.

The first one shows the voltage dependence on time  V(t)  also known as **action potential**. It can be distinguished the depolarization, plateau and repolarization phases of the action potentail of a cardiac cell. 

The second reffers to the **fast inward current ($I_Na$)**. This one has a very brief downward (inward current) spike that is triggered when the membrane voltage reaches around -70 mV. This is caused by the big increase in sodium channel conductance **($g_Na (t) $)**. This is related simultaneously with the last plot; the opening and closing of the m and h gates. 

The third plot shows the time dependent outward current **($I_K1$)** and the time independent outward current  **( $I_x1$ ) **. 

The fourth plot gathers both the m gate and the h gate. The opening of m gate coincides with the spike from the  **fast inward current ($I_Na$)** seen in the second graph. The m gate is open during the plateau and is closed when the h gate opens. 

The last plot refers to the second slower inactivation gate j. This is a special characteristic of this model since the Hodgkin and Huxley does not include this variable.  The total ionic current in the Beeler-Reuter model is given by four currents, and the model uses eight variables.

![beelerreuter2](https://user-images.githubusercontent.com/39902241/42158670-68bdde56-7df1-11e8-9662-d92f4916b663.jpg)

## The Fitzhugh Nagumo model 

The following screenshot refers to the Fitzhugh Nagumo model  run by OpenCOR. There are two plots regarding the different parameters. 

In this case, since this model is an Empirical model which aims for a larger spatial and temporal scale only the V(t) voltage dependence on time and the W(t) recovery variable are plotted. 






