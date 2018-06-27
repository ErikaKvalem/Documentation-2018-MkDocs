# Documentation for the set-up of fenics+cbcbeat on Mac using Docker. 04/06/18

## 1.	Introduction:

This is a step by step explanation on how to install **The fenics project** and **cbcbeat** in Mac using **Docker**. 

The final aim of this whole process is to be able to use Fenics and cbcbeat to **run cell and 2D tissue simulations and visualize them.** 

Fenics can be installed in four different ways; using Docker, Ubuntu, Anaconda or from source. In this case *Docker containers* have been chosen. 

Other programs that are going to be also used along the process are **OpenCOR** and **Paraview** 

## 2.	Specifications:

macOS High Sierra. 
Version10.13.2 
MacBook Air 2014


## 3.	Docker:

Installing Docker is the first step of this process.  To download it and install it, use the following [link](https://www.docker.com/community-edition#/download) should be used: 


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

Furthermore, to check if Docker is correctly installed the command **“ docker run hello-world”** is ran as shown above. 

For more documentation on getting started with Docker use this [link](https://docs.docker.com/get-started/).

## 4. Fenics 

It is important to notice that Fenics is Python based so it is necessary to have Python installed in the machine before installing Fenics. It is important to download *Python 2* since it is the one working with cbcbeat. [Link](https://www.python.org/downloads/) to download it. 

For the installation of Fenics the following [link](https://fenicsproject.org/download/) should be used. 

First of all it is important to place ourselves in the terminal and know exactly where we are at every moment so we can find easily the solutions and documents that fenics will create. 
In this case we will create a folder that will be called **my-project** where all the output from fenics will be stored. Inside that folder I created a folder called **Demo** and placed myself in there. The command *cd* is used in the terminal to change directory. 

```
Erikas-MacBook-Air:~ erikakvalem$ cd my-project

Erikas-MacBook-Air:my-project erikakvalem$ cd Demo

Erikas-MacBook-Air:Demo erikakvalem$ docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared -w /home/fenics/shared quay.io/fenicsproject/stable:current
```

Now that we are at my-project inside the Demo folder we run the following line, that can be found at the last link provided before:


``` 
docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared -w /home/fenics/shared quay.io/fenicsproject/stable:current
```

This creates a volume (–v) that is shared between the machine we are working at **($(pwd):/home/fenics/shared)** and the docker cloud **(home/fenics/shared quay.io/fenicsproject/stable:current) **

After running that line this should be the output: 

```
FEniCS stable version image

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

```
fenics@0ca36cf2dd4f:~/shared$ python ~/demo/documented/poisson/python/demo_poisson.py 
Solving linear variational problem.
To view figure, visit http://127.0.0.1:8000
Press Ctrl+C to stop WebAgg server

```
As it can be seen in the shared directory now there are two files and if we check the folder we created before these files should be in there. One with extension **.pvd** and another **.vtu**. 

Before stopping it *(ctrl+c)*, we can open the URL:   http://127.0.0.1:8000 and visualize the output online. 

For better visualization [ParaView](https://www.paraview.org/download/)  will be used. Its installation is straight forward, however for better understanding of its functioning more information can be found in the [fenics tutorial](https://fenicsproject.org/documentation/) (page 27 for the first example) 

For running other demos, it can be checked that there are more demos in the demo directory by using the list command in the terminal (ls)

```
fenics@0ca36cf2dd4f:~$ cd demo/documented
fenics@0ca36cf2dd4f:~/demo/documented$ ls
auto-adaptive-poisson  hyperelasticity      nonmatching-interpolation  stokes-mini
bcs                    maxwell-eigenvalues  periodic                   stokes-taylor-hood
biharmonic             mixed-poisson        poisson                    subdomains
built-in-meshes        navier-stokes        singular-poisson           subdomains-poisson
cahn-hilliard          neumann-poisson      singular-poisson-rst       tensor-weighted-poisson
eigenvalue             nonlinear-poisson    stokes-iterative
fenics@0ca36cf2dd4f:~/demo/documented$ 

```

These are all the demos that can be called. We place ourselves inside the directory and call the demo.

```
fenics@0ca36cf2dd4f:~/demo/documented$ cd nonlinear-poisson/
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson$ ls
cpp  python
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson$ cd python/
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson/python$ ls
demo_nonlinear-poisson.py
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson/python$ python demo_nonlinear-poisson.py
Calling DOLFIN just-in-time (JIT) compiler, this may take some time.
--- Instant: compiling ---
```

In this case it can be seen we were not In the shared directory therefore we have to copy the files from the directory where they are stored by default into our machine by doing the following: 

```
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson/python$ ls
demo_nonlinear-poisson.py  mesh000000.vtu         nonlinear_poisson000000.vtu
mesh.pvd                   nonlinear_poisson.pvd
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson/python$ cp * /home/fenics/shared
fenics@0ca36cf2dd4f:~/demo/documented/nonlinear-poisson/python$ 
```

## 5. Cbcbeat

**Cbcbeat** is manly used in *computational cardiac electrophysiology*. This is the [main page](http://cbcbeat.readthedocs.io/en/latest/)
for the documentation. 
The installation of cbcbeat is however more tedious. The following [link](https://bitbucket.org/meg/cbcbeat/src/default/) is the main one for the installation.

To install it, first all the packages must be downloaded. For this purpose it is helpful to have/create a [BitBucket](https://bitbucket.org/dashboard/overview) account so the repository can be downloaded. 

After that, on the left side panel of the [web page for cbcbeat](https://bitbucket.org/meg/cbcbeat/src/default/) we have to click on **Downloads** and click on **Download repository**. This action will download a file *.zip* that must be uncompressed. Afer that I personally decided to save in the Desktop for convenience. This file is called **meg-cbcbeat-370fa4c4a62e** and in it, there are many files conerning cbcbeat and its installation. 
```
Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ ls
AUTHORS			bitbucket-pipelines.yml	joss
COPYING			build			sandbox
COPYING.LESSER		cbcbeat			scripts
Dockerfile		data			setup.py
INSTALL			demo			test
README.rst		doc	
```
Now we proceed to follow the steps that can be found in cbcbeat webpage in the  INSTALL section: cbcbeat/src/default/INSTALL

First step:
```
Erikas-MacBook-Air:Desktop erikakvalem$ cd meg-cbcbeat-370fa4c4a62e/
Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ sudo python setup.py install
Password:
```
Second step: 

```
Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ export PYTHONPATH=`pwd`:$PYTHONPATH 
```

Now we will verify the installation: 

```
Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ cd test
Erikas-MacBook-Air:test erikakvalem$ ls
README		conftest.py	unit
Erikas-MacBook-Air:test erikakvalem$ cat README
```
Te following step for managing to install cbcbeat is to go into The fenics project through the terminal as it was explained in section 4. However, it is not necessary to install it again. We should be able to just access The fenics project using this command in the terminal: 

```fenicsproject run```



After having done that ( The prompt should say something like: fenics@0ca36cf2dd4f:~/local$ ) we proceed to keep cbcbeat installation. It is important to notice that in the prompt says **local** not **shared**. 

*To be able to download the repository using the bitbucket account I needed some plugins such as: Mercurial, ssh. I leave the installation steps for those* 

``` 
fenics@0ca36cf2dd4f:~/local$ sudo apt-get install openssh-client
fenics@0ca36cf2dd4f:~/local$ ssh
fenics@0ca36cf2dd4f:~/local$ sudo apt-get update
fenics@0ca36cf2dd4f:~/local$ sudo apt-get install mercurial
fenics@0ca36cf2dd4f:~/local$ h
```
After this, in the following step we proceed to get the repository.
```
fenics@0ca36cf2dd4f:~/local$ hg clone https://ErikaSimula@bitbucket.org/meg/cbcbeat 

```

If we check it afterwards should look like this: 
``` 
fenics@0ca36cf2dd4f:~/local$ ls
cbcbeat
```
The following commands are to test the installation with a demo: 

```fenics@0ca36cf2dd4f:~/local/cbcbeat$ cd test
fenics@0ca36cf2dd4f:~/local/cbcbeat/test$ py.test -m "fast" -v
```


To make it easier to use this on a daily baisis it is recommended to build a Docker image containing fenics and cbcbeat. 
This is done by using the lines of code that are in the file called **Dockerfile** that can be found in *Source* directory in the main page for [cbcbeat](https://bitbucket.org/meg/cbcbeat). It goes as follows: 


```# Builds a Docker image for reproducing the results in the wetting and drying
# adjoint paper by Funke et.al

FROM quay.io/dolfinadjoint/dolfin-adjoint:latest
MAINTAINER Simon Funke <simon@simula.no>

USER root
RUN sudo apt-get update && sudo apt-get -y install mercurial

USER fenics
RUN hg clone https://bitbucket.org/meg/cbcbeat
RUN cd cbcbeat && pip install . --user

USER root
```

After that, what is left is to do a push to a public repository on Docker: 


```
docker push _ _ _ _ _ _ /cbcbeat
```

In the dashed line the user name in Docker should be written. 

Then run in the terminal:

```
1.- docker pull _ _ _ _ _ _ /cbcbeat

2.-docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared -w /home/fenics/shared _ _ _ _ _ _ /cbcbeat
```


To see the full process done in the terminal during the installation of cbcbeat and the expected output of the commands go to **Terminal Code** in this documentation. 

## Open COR 

## ParaView








 







































