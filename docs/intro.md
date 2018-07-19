# 1. Introduction

The purpose of this documentation is to better understand **simulations of atrial fibrilation**. For this purpose cardiac cell models are run using **The fenics project** and **Cbcbeat** (**python**). 

This documentation will help to better understand throguh step by step explanation, **how to perform the simulations**, going from **atrial geometries** to the **simulation output**. 

**Atrial fibrilation (AFib)**  is a  type of **supraventricular tachycardia**. It is a pathological state of the heart caused by irregular heartbeat of the atria. This causes the blood not to be moved effectely to the ventricles and therefore it can lead to **clots, strokes and heart failure**. **AFib** is the **most common abnormal heart rythm** affecting 2% of the population in Europe and North America. 

Since the mechanisms underlying **AFib** are poorly understood it is very helpful to use simulations based on **mathematical models** of the **cardiac cells** that will allow a better understanding of the process and eventually lead to new solutions for this pathology. **[i]**

In this documentation, a detailed explanation on how to install **The fenics project** and **Cbcbeat** in **Mac**using **Docker** is given. Moreover, some highlited **cardiac cell models** are described. It can also be found a tutorial on cbcbeat for 2 demos explaining what the code is doing from a general point of view. Furthermore, **OpenCOR** and **ParaView** visualization of the solutions ir provided. 

The development of this repository has been done in the context of [**SysAFib project**](https://www.simula.no/research/projects/sysafib-systems-medicine-diagnosis-and-stratification-atrial-fibrillation)**[ii]** at [**Simula Research Laboratories**](https://www.simula.no/) **[iii]** during the summer 2018. The project will be presented at [**VPH2018**](http://vph-conference.org/)**[iv]**








