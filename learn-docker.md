## Learning Docker

- start-date: 15-sept-2021
- end-date: ???
- instructor: Mosh Hamadani


### Getting started.

A comprehensive course that will teach you how to work with docker from basic to more advance user.
And will deploy application using docker both front-end, backend, and database.

What you need to know
- atleast 3 months of programming experience.
- atleast have concept of front-end, backend, apis, and databases.
- familarity with basic git commands.

How to take this course
- while listening to the lectures you should take notes as well - because this course is highly practical
- after each course repeat the steps by your own.


### Introduction to docker

Agenda
- What is docker
- Virtual Machines vs containers.
- Architecture of docker.
- Installing docker.
- Development workflow.


### What is docker

A plateform for building, running and shipping applications in a consistent manner.
because if your application is running on it can run and function same way on other machines.

> Common Developer Argument: It is working on my machine.

Possible reasons of above problem
- Files and libraries missing.
- software version mismatch. eg. Required: Node v14 but other machine is running Node v12 
- different configuration settings.

This is where docker comes into action.

With the help of docker we can package our application what it needs and run it anywhere on any machine - that runs docker.


It also helps other team members who have joined your team for setting up the development environment and waste half of the day

Docker with then automatically mannages the dependencies the application requires and also creates an isolated environments - called 'container'
and this is the beauty of docker - these isolated environments allows different versions of software side by side. 


It also enable us to remove those depencies that are not required when the project is done, with out messing up the things :)

In a nutshell

> Docker is a solution for consistently build, run, and ship applications...

#### Virtual Machines vs Containers

Container
- an isolated environment for running an application. 

Virtual Machines
- An abstraction of machine or physical hardware.



[ linux ] - [ win ] - [ mac ]
               |
         [ Hypervisor ]
               |
         [ Hardware ]



With the help of hypervisor we can run different virtual machines. And on each virtal machine we can install OS of our own choice.

Hypervisors
- Virtual box
- Vm ware
- hyper-v (windows-only)

virtual machines are helpfull but they have different problems with current model.
- each vm needs a full blown os - memory and cpu wastage, licenced, patched, and moniter.
- slow to start
- resource intensive.


Containers
- gives us same kind of isolation that vm provides.
- are more lightweight.
- use the OS of the host.
- start quickly.
- need less hardware resources.





		


### The linux command line


### Building images


### Working with containers


### Running multi container application


### Deploying application




## Progress Track

ch-1    15-Sept-2021
ch-2.3  15-Sept-2021 

