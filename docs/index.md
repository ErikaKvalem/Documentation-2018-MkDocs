# Documentation for the set-up of fenics+cbcbeat on Mac using Docker. 04/06/18

## 1.	Introduction:

This is a step by step explanation on how to install The fenics project and cbcbeat in Mac using Docker. 
The final aim of this whole process is to be able to use Fenics and cbcbeat to run cell and 2D tissue simulations and visualize them. 
For this purpose, several approaches can be taken. Fenics can be installed in four different ways; using Docker, Ubuntu, Anaconda or from source. In this case Docker containers has been chosen. 

## 2.	Specifications:

macOS High Sierra. 
Version10.13.2 
MacBook Air 2014


## 3.	Docker:

Installing Docker is the first step of this process.  To download it and install it, the following [link](https://www.docker.com/community-edition#/download) should be used: 


The whole concept of Docker is new and very abstract. Docker is a container platform using images and containers. What it will be done in this tutorial is download the image of the fenics project and start a container with it. This container it is going to be shared between the machine and the cloud. 

Moreover, a Docker ID should be created so afterwards Docker Hub can be used only to download or upload repositories. 

Something to take into account is that the only thing that will appear in the screen concerning Docker is a small figure in the top right corner that will show a small panel.
![alt text](https://github.com/ErikaKvalem/Documentation-2018-MkDocs/blob/master/Screen%20Shot%202018-06-04%20at%208.45.48%20AM.png)
