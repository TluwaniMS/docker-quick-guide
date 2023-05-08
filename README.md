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
