# Docker quick guide.

Docker is a platform that facilitates the development, transfer, and execution of software applications.

With Docker, you have the capability to decouple your application from your infrastructure, and package and execute it within a loosely isolated environment known as a container;

by enabling isolation, it becomes possible to run multiple containers concurrently on a single host.

# Docker Architecture

Docker uses a client-server architecture.
- Docker containers are built, run, and distributed by the docker daemon, which communicates with the docker client.
- The means of communication between the docker client and daemon involves the use of a REST API, either through a network interface or UNIX sockets.

## Docker daemon (dockerd)
- The docker API requests are received and managed by the docker daemon, which oversees various docker objects like images, containers, networks, and volumes.

## Docker client
- The main method of interacting with Docker for users is through the Docker client.

## Docker registries
- Docker images are stored in the Docker registry.

## Docker images
- A docker image is a read only template with instructions for creating a docker container.

## Docker containers
- A container is a runnable instance of an image.
- When a container is created or initiated, its image and any accompanying configuration choices define it.

# Deployment Strategies:

### Bare Metal:

- No Virtualisation, the application or service is deployed directly onto the machine.


![Bare Metal Image](https://github.com/TluwaniMS/docker-quick-guide/blob/master/supporting-images/Hardware.png)

### Virtual Machines:

- The hardware is virtualised so multiple operating systems can be isolated on the machine.

![Virtual Machine Image](https://github.com/TluwaniMS/docker-quick-guide/blob/master/supporting-images/Virtual_Machines.png)

### Containers:

Virtualised operating system
- Libraries and operating applications are isolated with their own namespace

![Docker Container Image](https://github.com/TluwaniMS/docker-quick-guide/blob/master/supporting-images/Containers.png)

# Basic Dockerfile Instructions Guide:


A "Dockerfile" is a textual file that comprises all the instructions that a user wants to execute in order to build an image.


### FROM:
The `FROM` instruction designates the Parent Image used as the foundation for the following instructions, allowing you to build upon it and establish a new build stage.


### COPY:
`COPY <src>... <dest>`
The `COPY` command is used to duplicate files or directories from the source location`<src>` and incorporate them into the container's filesystem at the specified destination path `<dest>`.


### ENV:
`ENV <key>=<value>`
The `ENV` directive is used to assign the environment variable `<key>` with the value `<value>`. This value remains accessible to all subsequent instructions within the build stage and can also be conveniently substituted inline in numerous cases.


### WORKDIR:
`WORKDIR /path/to/workdir`
The usage of the `WORKDIR` instruction in a Dockerfile establishes the working directory for subsequent instructions like `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD`.


### CMD:
`CMD ["executable","param1","param2"]`
The primary objective of a `CMD (Command)` is to establish default settings for a running container. These settings can encompass an executable command or exclude it altogether. A Dockerfile can only contain a single `CMD` instruction.


### RUN:
`RUN <command>`
The `RUN` instruction performs the execution of commands within a new layer, which is stacked on the existing image, and subsequently records the outcomes.


### EXPOSE:
`EXPOSE <port> [<port>/<protocol>]`
The `EXPOSE` command notifies Docker that the container will be listening on designated network ports during runtime. It's important to note that the `EXPOSE` instruction doesn't actively publish the ports. Instead, it serves as a form of communication or documentation between the image builder and the container operator, indicating which ports are intended to be made public.
