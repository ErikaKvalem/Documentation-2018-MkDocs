# Documentation for the set-up of fenics+cbcbeat on Mac using Docker. 04/06/18

## 1.	Introduction:

This is a step by step explanation on how to install The **fenics project** and **cbcbeat** in Mac using **Docker**. 
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

Docker is going to be controlled using commands at the terminal. Looking like this: 
```
Erikas-MacBook-Air:~ erikakvalem$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

Erikas-MacBook-Air:~ erikakvalem$ 
```

Furthermore, to check if Docker is correctly installed the command “ docker run hello-world” is ran as shown above. 

For more documentation on getting started with Docker use this [link](https://docs.docker.com/get-started/).
## 4. Fenics 

It is important to notice that Fenics is Python based so it is necessary to have Python installed in the machine before installing Fenics. It is important to download Python 2 since it is the one working with cbcbeat. [Link](https://www.python.org/downloads/) to download it. 

For the installation of Fenics the following [link](https://fenicsproject.org/download/) should be used. 

First of all it is important to place ourselves in the terminal and know exactly where we are at every moment so we can find easily the solutions and documents that fenics will create. 
In this case we will create a folder that will be called my-project where all the output from fenics will be stored. Inside that folder I created a folder called Demo and placed myself in there. The command cd is used in the terminal to change directory. 

```Erikas-MacBook-Air:~ erikakvalem$ cd my-project
Erikas-MacBook-Air:my-project erikakvalem$ cd Demo
Erikas-MacBook-Air:Demo erikakvalem$ docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared -w /home/fenics/shared quay.io/fenicsproject/stable:current
```
Now that we are at my-project inside the Demo folder we run the following line, that can be found at the last link provided before:
```docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared -w /home/fenics/shared quay.io/fenicsproject/stable:current
```

This creates a volume (–v) that is shared between the machine we are working at **($(pwd):/home/fenics/shared)** and the docker cloud **(home/fenics/shared quay.io/fenicsproject/stable:current)**.

After running that line this should be the output: 

```
# FEniCS stable version image

Welcome to FEniCS/stable!

This image provides a full-featured and optimized build of the stable
release of FEniCS. Both python2 and python3 versions are available.

To help you get started this image contains a number of demo
programs. Explore the demos by entering the 'demo' directory, for
example:

    cd ~/demo/documented/poisson/python/
    python3 demo_poisson.py
fenics@a3dc1c817b2b:~/shared$ 
```
This should be the last line: fenics@1b4bc5a18810:~/shared$

The last line tells us that we are inside the fenics project with an specific ID and that is shared between the server and the machine (the host). Fenics is being run inside Docker. 
A demo can be run to prove fenics is working properly. 
Using the following command: 
```python ~/demo/documented/poisson/python/demo_poisson.py 
```

**INSERT HERE THE OUTPUT ON THE TERMINAL FROM THE DEMO**

As it can be seen in the shared directory now there are two files and if we check the folder we created before these files should be in there. 
![alt text](https://github.com/ErikaKvalem/Documentation-2018-MkDocs/blob/master/Screen%20Shot%202018-06-04%20at%209.49.19%20AM.png)

Before stopping it, we can open the URL:   http://127.0.0.1:8000 and visualize the output online. 

![alt text](https://github.com/ErikaKvalem/Documentation-2018-MkDocs/blob/master/Screen%20Shot%202018-06-04%20at%209.01.34%20AM.png)

For better visualization ParaView will be used. Its installation is straight forward, however for better understanding of its functioning more information can be found in the fenics tutorial (page 27 for the first example) 

Paraview Download link: https://www.paraview.org/download/ 

Fenics tutorial: https://fenicsproject.org/documentation/

For running other demos, it can be checked that there are more demos in the demo directory by using the list command in the terminal (ls)







