This article is meant to give a brief understanding of docker, it's components and use.

**Docker**
Docker is a software platform that simplifies the process of building, running, managing and distributing applications.

A **Docker container** is a loosely isolated environment running within a host machine’s kernel that allows us to run application-specific code along with it's dependencies.
Docker runs on top of the original host machine kernel.

The **Kernel** is the key program or software at the core an operating system with complete control of a computer or machine.

**Docker Engine** is an open source containerization technology for building and containerizing your applications and it consists of :-
- Docker Server or Docker daemon
- Docker Engine Application Program Interface (API)
- Docker Command Line Interface (CLI)

The diagram below explains their relationships.
![Docker](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h8o8njzc7w2h8ydnndd2.png)


**_How are containers created?_**
_In programming terms_: Docker containers can be described as objects that are created by a class in docker called _Docker images_. 

**_A Docker Image_** is an executable package that contains a  read-only template with set of instructions used to build a container. When these instructions are executed, it creates a _Docker container_. It can be compared to a snapshot used in a Virtual machine (VM) environment.

These instructions defines all what the container needs, this includes the container code, libraries, environment variables, configuration files, and more. Hence, a _**docker container**_ can also be thought of as an instance of the set of instructions defined in a docker image running on a host machine.

![instance](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y2lzkvwbtjpikfiq8yhp.png)

It is also important to understand the relationship between a docker image and a docker container. It is not always a _one to one_ relationship. It can be _**one to one**_ or _**one to many**_, that is, many docker containers can be created from one docker image.

![Relationship](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/aq7fivub21islzgzny5n.png)

Let's create a docker container
- Install [Docker desktop here] (https://docs.docker.com/desktop/)
- Choose your OS on the left menu and follow the installation instruction

![install](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xc6fzt8voto5ylzyrzqu.png)

**_Quick getting started docker commands_**
```bash
# Search the docker hub for available ubuntu images
docker search ubuntu

# Create a new container base on the ubuntu image
docker create -it --name=fooo ubuntu bash

# List of started containers
docker container ls

# List created containers
docker container ls -a

# Start a created container
docker start fooo

# Start a interactive mode (-it) on the container
docker attach fooo

# Run a command in a new container
docker run --name=bar -it ubuntu bash

# Exit interactive mode
Ctl q+p

# Check container history
docker logs fooo

# Stop container
docker stop fooo

# Remove container
docker rm fooo

```
How to create docker containers fooo & bar from a ubuntu image

![bar](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2wo4lfbd64emku2stbbd.png)

Desktop view of docker containers fooo and bar

![containers](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qb4b9nb5ay8405jnbyir.png)

**Dockerfile**
A _Dockerfile_ outlines instructions for how an image will create a container. It is a text document that contains all the commands a user could call on the command line to assemble an image.

![dockerfile](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tp0v4trzea925923r89t.png)

As always, I look forward to getting your thoughts on this article. Please feel free to leave a comment!