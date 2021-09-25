# Learning Docker

- start-date: 15-sept-2021
- end-date: ???
- instructor: Mosh Hamadani


## Getting started.

A comprehensive course that will teach you how to work with docker from basic to more advance user.
And will deploy application using docker both front-end, backend, and database.

What you need to know
- atleast 3 months of programming experience.
- atleast have concept of front-end, backend, apis, and databases.
- familarity with basic git commands.

How to take this course
- while listening to the lectures you should take notes as well - because this course is highly practical
- after each course repeat the steps by your own.


## Introduction to docker

Agenda
- What is docker
- Virtual Machines vs containers.
- Architecture of docker.
- Installing docker.
- Development workflow.


### What is docker

A plateform for building, running and shipping applications in a consistent manner.
because if your application is running on your machine, it can run and function same way on other machines.

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


** Important **
Docker uses client server architecture. It has a client component that talks to the server using restfull APIs. The server is also called Docker Engine (or deamon), that runs in the background and is responsible for doing the actual work.

Using docker, we can bundle an application into an image. Once we have that image, we can run it on any machine that runs docker.

An image is bundle of everything needed to run an application. That includes a cutdown OS, a runtime environment (eg. Node, Python, JVM, etc), application files(code), third parties libraries, drivers, environment variables etc...

To bundle an application into an image, we need to create a docker file. A docker file contains all the instructions needed to package up an application into an image.

We can share our images by publishing them on Docker registory. The most popular Docker registory is Docker HUB.

> Remember: the images and containers in the Windows world are invisible to the linux world. You would needs Windows containers only if you need an image that starts from Windows.


#### Virtual Machines vs Containers

Container
- an isolated environment for running an applications. Its essentailly an operating system process with its own file system. 

Virtual Machines
- An abstraction of machine or physical hardware or hardware resources. With the help of hypervisor we can create and manage virtual machines.
 
kernal
- It is the core of the operating system. It is the part that manages applications and hardware resources. Different OS kernal have their own different APIs. That is why we can not linux application on windows and viceversa. 


[ linux ] - [ win ] - [ mac ]
               |
         [ Hypervisor ]
               |
         [ Hardware ]


For running docker on windows - First, enable feature windows subsystem for linux. Because now windows makers ships 'linux-kernal' along with 'windows-kernal'


Hypervisors
- Virtual box
- Vm ware
- hyper-v (windows-only)

With the help of hypervisor we can run different virtual machines. And on each virtal machine we can install OS of our own choice.


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


## The linux command line

Why linux command line?
  Because Docker is build on basic of linux concepts. 
  Most docker tutorials are based on linux commands.
  
Learning linux is like learning english.

### Linux distributions/distros

- linux is open-source - and due to the power of open-source, anyone can change, enhance, customize, ship by his/her own way. That is why 1000 of distributions are out there in the market having their own different flavours and taste.
- Different individuals and communities have tailored linux by their own version of systems - they call them distros.
- Each distribution have some specialized reson behind its construction eg. Running servers, Running super computers, Running small embeded devices, Running desktop etc

Famous distros
- Ubuntu
- Debian
- Alpine
- Fedora
- CentOs

Most of the distributions shares same set of commands, but not all - Be aware of the difference incase of package managers, user-management, and so on. 

### Running Ubuntu

1. Goto docker hub and search for ubuntu

```sh
# check installed version of docker
$ docker -v

# download the image from docker hub
$ docker pull ubuntu

# run image - download if not available locally
$ docker run ubuntu




```

when we run ubuntu image - behind the scene - docker created container using that image, since we didn't interact with the container, container shuts down immediately.

proof
```sh

# list all the docker processes.
$ docker ps -a

# run docker in interactive mode.
$ docker run -it ubuntu

```


### Package Managers

These days most of the Operating systems and development tools comes with the package mangers.
eg. pip, npm, yarn, maven, choco, apt, apt-get, Nuget, brew, etc...


apt - advance package tool - is a package manager for debian based distributions

```sh
# list all the packages installed/not-installed from package database.
$ apt list 

# search the package by its name from package database.
$ apt search <package-name>

# updates the package database.
$ sudo apt update

# install package by its name
$ sudo apt install <package-name>

# un-install package by its name
$ sudo apt uninstall <package-name>
```

### Linux file system

in linux or windows or other operating system our files are organized in the form of tree like structure - hierarical structure.

c:/
  Program Files
  Windows
  Users

/
  usr/
  bin/      contains binary programs
  home/
  etc/      contains all editable configuration files for different applications.
  boot/     contains all files related to boot process
  dev/      contains all devices related information
  lib/
  proc/     contains all processes information
  root/
  var/      contains files that are changed frequently eg. log files etc...

In the world of linux every-thing is a file - devices, processes, pipes, network sockets and so on...


### Navigating between directories

```sh
# navigate between directories
$ cd /etc

# navigate one directory back
$ cd ../

# navigate to users home directory
$ cd ~
```

### Working with files and directories

```sh
# creating new directory
$ mkdir temp

# creating new file
$ touch file

# re-naming files and directories
$ mv old-name new-name

# moving file here and there
# mv <source> <destination>

# removing file
$ rm file

# removing empty directory
$ rmdir temp

# removing directory with files
$ rm -r temp
```
### Editing and viewing files

```sh
# editing file within terminal using basic terminal based editor - nano
$ nano <filename>

# editing file within terminal using advance text editor - vim
$ vim <filename>

# dump the content of the file to the terminal
$ cat <filename>

# display the file's content in paginated format - quite useful when the file text is large
$ more <filename>

# displays the file's content in a more convinent fashion - you can scroll up and down easilly
$ less <filename>

# displays the top 5 lines of the file
$ head <filename>

# displays the trailing 5 lines of the file
$ tail <filename>

# displays top 10 lines
$ head -10 <filename>
```
### Redirection





## Building images

## Working with containers


## Running multi container application


## Deploying application

