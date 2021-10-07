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

# running an existing docker container.
$ docker start -t <container-hash>

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
bin/ contains binary programs
home/
etc/ contains all editable configuration files for different applications.
boot/ contains all files related to boot process
dev/ contains all devices related information
lib/
proc/ contains all processes information
root/
var/ contains files that are changed frequently eg. log files etc...

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

in computer science
keyboard is considered as STD-INPUT and
moniter is considered as STD-OUTPUT devices

but we can chage the direction of that sources - and that concept is called as redirection.

```sh
# redirect standard output to the file
$ ps -ef > processes.info

# piping the result of one command into another
cat /etc/passwd | cut -d ":" -f 1 | sort > users.txt
```

### Searching for text in files.

grep - global regular expression print

```sh
# do case insensitive search on /etc/passwd
$ grep -i root /etc/passwd

# search for pattern in current directory
$ grep -ir hello .

$ grep -i development /usr/share/common-licenses/GPL-3

$ grep -n "^GNU" /usr/share/common-licenses/GPL-3

```

^ - starts with eg. ^GNU
$ - ends with eg. the$
. - any character eg. ..cept
[] - range eg. t[wo]o
[^] - not in range eg. [^c]ode

starts with capital letter - "^[A-Z]"

### Finding files and directories

```sh
# list all the files with in current directory recursively
$ find

# list only the directories recursively
$ find -type d

# list only the files with name
find -type f -name "*.txt"

find / -type f -name "*.py" > python-files.txt
```

### Chaining commands

```sh
# chaining commands using semicolon - all the chained commands will be executed, no matters which commands fails to execute.
$ mkdir test; cd test; echo "done"

# chainging the commands using && 'and' operator - here next command will be executed if the previous command runs successfully - retruns 0
$ mkdir test && cd test && echo "done"

# chain commands using '||' or operator
$ mkdir test || echo "directory already exists..."

# piping the output of one command and give as a input to another command.
$ ls /bin | less
```

### Environment variables

we having variables in different programming languages same as we have environment variables. we use environment variables to store application configuration information.

```sh

# displays list of environment variables.
printenv

# displays list of environment variables.
env

# displays the variable's value by its name
printenv PATH

# another way to print or see environment variables.
$ echo $PATH

# setting up the environment variable value. - this env varible will only be available to current user session
$ export DB_USER=mosh

```

In order to make environment variables persistent - write them in .bashrc files

```sh
$ echo DB_NAME=students-db >> ~/.bashrc

$ source ~/.bashrc
```

> Note: never store any sensitive information in environment variables eg. db passwords etc...

### Managing processes

A process is the instance of running program.

in linux/unix world to find the list of processes or programs we use the following commands

```sh
# list the current running processes
$ ps

# runs a background process
$ sleep 100 &

# kill the process by its process id
$ kill -9 <pid>
```

### Managing users

- useradd - For adding user
- usermod - For modifying user info
- userdel - For deleting user
- adduser - More interactive command for adding user.

```sh

# will create user jhon and create its home directory - for varifying check /etc/passwd file
$ useradd -m jhon

# change the shell of user jhon to bash
$ usermod -s /bin/bash jhon

```

```sh
# syntax for executing command against container id
$ docker exec <container-hash> <command>

# attach to the container in interactive mode.
$ docker exec -it fc321 bash

# attach to the container as jhon in interactive mode.
$ docker exec -it -u jhon fc321 bash
```

### managing groups

similarly like managing users we have commands for managing groups

- groupadd
- groupmod
- groupdel

in linux every user have its

- primary group - only one
- secondary/suplimentry group - zero or more

this is because when user creates a file is belongs to the single user and single group

```sh
# add the group by name - to verify view /etc/group
$ groupadd developers

# add jhon to the developers group.
$ usermod -G developers jhon
```

### user permissions

x - execute
r - read
w - write

- - for add

* - for remove
    u - user
    g - group
    o - others

Numerical weights
4 - read
2 - write
1 - execute

```sh
# check file permissions
$ ls -l

# add execute permission
$ chmod u+x <file>

```

## Building images

The first set to build and deploy application using docker is to build images. So, having solid understanding of images is crucial.

In this section

- Creating docker files.
- versioning images
- sharing images
- saving and loading them
- reducing image size
- speeding up builds

Images vs containers

container

- container is running instance of an image.
- provides an isolated environment to ran application(s) - a kind of virtual machine.
- can be stopped and restarted just like VMs
- Is just a process - special kind of process

Note: A container gets the file system from its image. But each container has its own right layer. So what we do in one container is invisible to other containers.

In a nutshell what ever happens inside one container universe - is invisible to other container universe. Although there is some file sharing mechanism, that will be discussed later.

image

- an image is simply package of all of its dependencies eg. lib, configs, etc...
- an image contains every thing that application needs to run. eg. cut-down OS, third parties libraries, application files and environment variables. - in nutshell it contains all the configuration settings required to run an application - and typicaally can start a container from it.

Dockerizing the react application.
Steps

1. Install Node
2. Download App dependencies `$ npm install`
3. Start the application `$ npm start`

### Docker file instructions

the first step in dockerizing the application we create a docker file of it. A docker file contains a set of instruction for building an image.

Docker Instruction set

- FROM specifies base image
- WORKDIR working directory to work with
- COPY used to copy files
- ADD
- RUN used to run operating system commands
- ENV for setting env variables
- EXPOSE for telling docker to run appilcation on given port
- USER for specifying user that can run the application
- CMD specifies the commands should be executed when we start the container.
- ENTRYPOINT

### Choosing the right base image

base image is usually cut-down operating system OR operating system with runtime environment.

```dockerfile

FROM node:16.10.0-alpine3.13

```

Note: if you write node:latest it will download the latest version everytime and it is not practical at all...

```sh
# build image from docker file.
$ docker build -t <tag-name> <source-dir>

# build an image from docker file present in the current dir and name it to 'demo-app'
$ docker build -t demo-app .

# list available docker images locally
$ docker images

or

$ docker image ls

# running the build image.
$ docker run -it demo-app

# running the build image with shell.
$ docker run -it demo-app sh

```

```dockerfile

FROM node:14.6.0-alpine3.13
WORKDIR /app
COPY . .

```

Note: For any image that exists outside the docker hub repository - we have to mention its full path

> `Buster` images are linux-v10 images eg. 14.16.0-buster

eg. `FROM mcr.microsoft.com/dotnet/core/sdk:3.1`

Note: ADD command will have 2 magic in it.

Note: When you do not specify the version of the image docker by default pulls out latest image

1. automatically uncompress the compressed file when you want to add.
2. having support to copy files from some url.

After some changes in the dockerfile you can easilly rebuild the entire application.

```sh

# re-build the application.
$ docker build -t react-demo .
```

when we execute the build command, docker client sends the content of the mentioned directory to the docker engine (build context). And then docker engine executes the commands mentioned in the dockerfile oneby one - that is by docker doesn't have access outside of the mentioned directory during time of build.

`COPY <context-file/dir> <image-dir>`

`COPY ["<file1>", "<file2>", "<image-dir>"]`

When we spcify the WORKDIR then we can then specify relative paths to copy with reference to WORKDIR

### Excluding files and directorities

```.dockerignore

node_modules/

```

ignoring files and directories that are un-necessary would be very helpfull in reducing the size of the context directory, that we sent to docker engine. It saves alot of time in sending lots of file and ultimately speeds deplying and building apps.

### Running Commands

RUN directive is used to specify the commands that should be run. It could be any possible linux command that is required after copying the source files.

```dockerfile
# will install node-modules
RUN npm install
```

### Setting environment variables.

```dockerfile

ENV ENVIRONMENT=production
ENV BASE_URL=http://www.api.github.com/repos

```

### Exposing Ports

when we try to start the application inside the container it will open port inside the container itself - Not on the host.

So the the same machine we can have multiple containers running the same image. All the containers will be listening to the same port. Port on the host machine is not going to be mapped with these containers.

```dockerfile
EXPOSE 3000
```

the above command will not bind the host port with the container port - but it the good to write it for better documentation

### Setting the user

by default docker runs on our application by root user - that has the highest previliges. That can create security holes in our system. So inorder to run the application we have to create the user with limited previliges.

```sh

# for demonstration purposes
$ docker run -it alpine

# create group app.
$ addgroup app

# creating system user with group
$ adduser -S -G app app

# displays the groups of the app user - cross validate
$ groups app

```

```dockefile
RUN addgroup app && adduser -S -G app app
USER app
```

### Defining Entry points

Shell form

```dockerfile
CMD npm start
```

Exec form - `best practice`

```dockerfile
CMD ["npm", "start"]
```

since the command instuction is the entry point command. so using multiple CMD instuction will not take effect - only the last one. So it is better to have single one.

Difference between RUN and CMD

- RUN command is executed at the time of building the image, build time instruction
- While CMD command is run time instruction. It is executed when we start the container.

Note: when ever we supply the CMD instruction it will be replced by the command while starting the container eg. `$ docker run image-name sh`

here sh will be repaced by the CMD if passed from back, otherwise CMD will be executed.

Note: we can always overwrite the the default command when starting the container.

We can not easilly overwrite ENTRYPOINT when running the container until we pass some arguments.

```sh
$ docker run demo-app --entrypoint <cmd>
```

In practice we always use ENTRYPOINT when we are sure that 'this is the command' should always be executed when we need to start the container - no execption

while for CMD instruction we always have flexability to overwrite

```dockerfile
FROM node:14.16.0-alpine3.13
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
COPY . .
RUN npm install
ENV BASE_URL=https://api.github.com/
EXPOSE 3000
ENTRYPOINT ["npm", "start"]
```

### Speeding up builds

Concept of Layers in docker images

- an image is collectively collection of layers.
- you can thing of layers as seperate filesystem.

All the instuctions sepertely in the dockerfile could be treated as single layer

```
# get the layers information of an image
$ docker history <image-name>
```

Docker has the optimization mechanism built into it. So next time we tell docker to build the image. It looks for the first instuction and see if the instruction is changed or not. If it is not changed, it is not going to rebuild this layer, it is going to reuse it from cache. Docker do the same process for every instruction it reads from dockerfile.

But for the COPY instruction it sees the actual content of the directory and files - it any of the line changes - docker re-runs the current instruction all the preceding instructions.

Optimized docker file for faster builds.

```dockerfile
FROM node:14.16.0-alpine3.13
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
ENV BASE_URL=https://api.github.com/
EXPOSE 3000
CMD ["npm", "start"]
```

#### Important To Note - _Optimization Technique_

We should organize the dockerfile in a manner that instruction that are quite often changes should come at last.

dockerfile

stable-instructions -----> changing-instructions

### Removing images

```sh
# auto remove all the dengling images
$ docker image prune

# remove all stoped containers from $ docker ps -a
$ docker container prune

$ docker image rm <image-id>
or
$ docker image rm <image-name>
```

### Tagging the images

```sh
# tagging an image while building it
$ docker build -t react-demo:1.2.2 .

# tagging an image after its build
$ docker image tag <image-id> <tag>
```

> Note: it doesnt mean that image with latest tag is actually the latest image.

### Sharing images.

0. Goto docker hub.
1. Create account it - its totally free.
2. Create new repository.
3. `$ docker login`
4. `$ docker push <image-name>`

### Sharing images without dockerhub

```sh
# saving the image
$ docker image save -o react-app.image.tar react-app:v3

# loading the saved image
$ docker image load -i react-app.image.tar

# for getting help
$ docker image save --help
$ docker image load --help
```

### Chapter summary

#### Docker file instructions

- FROM # to specify the base image
- WORKDIR # to set the working directory
- COPY # to copy files/directories
- ADD # to copy files/directories
- RUN # to run commands
- ENV # to set environment variables
- EXPOSE # to document the port the container is listening on
- USER # to set the user running the app
- CMD # to set the default command/program
- ENTRYPOINT # to set the default command/program

#### Image Commands

```sh
$ docker build -t <name> .
$ docker images
$ docker image ls
$ docker run -it <image> sh
```

#### Starting and Stopping containers

```sh
docker stop <containerid>
docker start <continerid>
```

#### Removing containers

```sh
$ docker container rm <containerID>
$ docker rm <containerID>
$ docker rm -f <containerID>        # to force the removal
$ docker container prune            # to remove stopped containers
```

#### Volumes

```sh
$ docker volume ls
$ docker volume create app-data
$ docker volume inspect app-data
$ docker run -v app-data:/app/data <image>
```

#### Copying files between host and container

```sh
$ docker cp <containerID>:/app/log.txt .
$ docker cp secret.txt <containerID>:/app
```

#### Sharing source code with containers.

```sh
$ docker run -v $(pwd):/app <image>
```

## Working with containers

In this section

- starting and stopping containers.
- publishing ports.
- viewing logs.
- executing commands in containers.
- removing containers.
- persisting data using volumes.
- sharing source code.

### Starting & stopping containers

```sh
# list docker images.
$ docker images

# running the container
$ docker run <image-name>

# list docker running processes
$ docker ps

# run container in detached mode
$ docker run -d <image-name>

# giving container name.
$ docker run -d --name <container-name> <image-name>

# you can start the stoped containers.
$ docker container start <continer-name>

```

### Viewing logs

viewing log is very important when debugging the application in such cases when our application produces exception and stops working etc...

```sh
$ docker logs <container-id>
or
$ docker logs <container-name>

# docker help
$ docker logs --help

# -t -> timestamp
# -n -> last n lines
# -f -> follow
$ docker logs -n 5 -t <container>
```

### Publishing ports

When you starts application inside the container it attaches to the container's OS, not to the host OS.

In order to map the host's PORT with the container PORT we do one-to-one mapping.

```sh
# run the container and binds host's PORT 80 with container's 3000
$ docker run -d -p 80:3000 <image>

```

### Executing command in containers

We know that when we start the container it executes the default command written in the docker file.

What if you want to execute the command in running container? while trouble shooting etc...

```ps
# executing command in running container
$ docker exec <container> <command>

$ docker exec c1 pwd
$ docker exec -it c1 sh

```

### Starting and Stopping containers

As we know the container is like light weight virtual machine. We can stop and restart it when every we want.

```sh
# stopping the container by its name.
$ docker stop c1
or
$ docker container stop c1

# starting the stopped container.
$ docker start c1
```

### Removing containers

```sh
# removing the stopped container.
$ docker rm <container>

# forcely remove the container.
$ docker rm -f <container>

# verifying...
$ docker ps -a | grep <container>

# removing all the stopped containers in one go.
$ docker container prune
```

### Container file system

Every container has its own filesystem that is invisible to the other container's filesystem.

So, we should never store our data in a container file system. - that what volumes are for.

### Persisting data using volumes

#### Volume

A volume is storage outside of the containers. It could be directory on the host or on the cloud

```ps
# displays help manual.
$ docker volume --help

# creating shared volume
$ docker volume create app-data

# view volume information
$ docker volume inspect app-data

# attaching volume to containers filesystem
$ docker run -d -p 4000:3000 -v app-data:/app/data <image>
```

volumes are right way to persist data in out dockerize applications, because we have different lifecycle for containers.

We can share volumes among different containers.
Deleting a container will not effect the data stored in volumes.

### Copying files between the host and the container.

sometime we want to copy files between the host and the container. For example we have .log file in the container and we have to analyze it on host.

```sh
$ docker cp <source> <destination>

# copy file from container to host
$ docker cp <container-id>:/path/app.log ~/temp

# copy file from host to container
$ docker cp ./secret.txt <container-id>:/path/
```

### Sharing source code

Publishing changes

- For production build a new image, tag it properly, and then deploy it.

when developing the application and if we want some change let say we want to change the title of our application. Build image and running it will be very time consumig. Copying the changed files is also pain in the butt when we are running multiple containers of the image.

The easy approch is to bind the host filesystem dirs to container's file system dirs. So this way when we change any file in host directory it is automatically reflected in the corresponding containers

```sh
# binding host file system with container's filesytems.
$ docker run -d -p 5000:3000 -v $(pwd):/app <image>
```

Note:
By this way we can simutaniously code and run container at the same time. When ever we change file it is reflected in the container.


#### Section Summary

Running containers

```sh
$ docker run <image>
$ docker run -d <image>              # run in the background
$ docker run —name <name> <image>    # to give a custom name
$ docker run —p 3000:3000 <image>    # to publish a port HOST:CONTAINER
```

Listing containers

```sh
$ docker ps      # to list running containers
$ docker ps -a   # to list all containers
```

Viewing the logs

```sh
$ docker logs <containerID>
$ docker logs -f <containerID>       # to follow the log
$ docker logs —t <containerID>       # to add timestamps
$ docker logs —n 10 <containerID>    # to view the last 10 lines
```

Executing commands in running containers

```sh
$ docker exec <containerID> <cmd>
$ docker exec -it <containerID> sh   # to start a shell
```

Starting and Stopping containers.

```sh
$ docker stop <containerID>
$ docker start <containerID>
```

Removing Containers

```sh
$ docker container rm <containerID>
$ docker rm <containerID>
$ docker rm -f <containerID>        # to force the removal
$ docker container prune            # to remove stopped containers
```

Volumes

````sh
$ docker volume ls
$ docker volume create app-data
$ docker volume inspect app-data
$ docker run -v app-data:/app/data <image>
```

Copying files between host and container
```sh
$ docker cp <containerID>:/app/log.txt .
$ docker cp secret.txt <containerID>:/app
````

Sharing source code with containers

```sh
$ docker run -v $(pwd)/src:/app/src <image>
```

## Running multi container application

## Deploying application
