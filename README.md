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


### ENV:
`ENV <key>=<value>`

The `ENV` command establishes the environment variable <key> and assigns it the value <value>.
This value will persist in the environment throughout all subsequent instructions during the build stage.

# Docker build:

The `docker build` command constructs Docker images by utilizing both a Dockerfile and a 'context'.

`docker build [OPTIONS] PATH | URL | -`

### Practice.

`NB!`

To proceed with the practice exercises, kindly make a copy of the provided [repository](https://github.com/TluwaniMS/docker-practice-project) by cloning it.

# Building a docker image:

Switch to the root directory of the `docker-practice-project` and run the following command:

```
docker —tag node-docker-practice:v1.0.0 .
```

### —tag / -t:
Image name and optionally a tag in the name:tag format

`.` :

The `“ . ”` Specifies the path where the Dockerfile will be found, in this case pointing to the current directory.

### Building a docker image using a git repository:

`NB!`

For this task, there is no requirement to clone the `docker-practice-project`.

Navigate to your terminal and run the following command:

```
docker build -t docker-practice:repo https://github.com/TluwaniMS/docker-practice-project.git
```

### Break down of URL:

`https://github.com/<repo-owner>/<repo>.git#<branch>:<directory-that-contains-dockerfile>`


# Docker Image management:

* ### List all images:

`docker image ls`

* ### Remove all unused images:

`docker image prune`

* ### Remove a specific image:

`docker image rm <image_identifier>`

* ### docker image history:

`docker image history <image_identifier>`

# Docker run:

* Generate and execute a fresh container using an image.

`docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`

* Generating a fresh container and assigning it a designated name.

`docker run —name <prefered_container_name> <image_name/image_id>`

* #### Run container in detached mode:

Execute the container in the background and display the identification number of the container.

`—detach / -d`

`docker run —name <container_name> -d <image_name/image_id>`

* #### Run a container  and automatically remove it when it exits:

`—rm`

`docker run —name <container_name> —rm <image_name/image_id>`

* #### Expose the port(s) of a container to the host system for publishing:

`—publish / -p`

`docker run -p <host_port>:<container_port> <image_name/image_id>`

# Docker container management:

* #### List all running containers:

`docker container ls / docker ps`

* #### List all active and inactive containers:

`docker container ls -a / docker ps -a`

* #### Rename a container:

`docker container rename <container_name/container_id> <new_name>`

* #### Remove all unused containers:

`docker container prune`

* #### Remove a specific container:

`docker container rm <container_name/container_id>`

* #### Stop a running container:

`docker container stop <container_name/container_id>`

* #### Start a stopped container:

`docker container start <container_name/container_id>`

* #### Inspect a docker container:

`docker container inspect <container_name/container_id>`

* #### Check container logs:

`docker container logs <container_name/container_id>`
  
# Docker Hub:

Docker Hub functions as a platform offered by Docker that facilitates the discovery and exchange of container images.

* #### Generating an image for a Docker repository:

`docker build -t <docker-hub-user-name>/<repo-name>:<tag> .`

* #### Uploading/Pushing an image to the repository:

`docker push <docker-hub-user-name>/<repo-name>:<tag>`

* #### Retrieving/Pulling an image from Docker Hub

`docker pull <docker-hub-user-name>/<repo-name>:<tag>`
  
# Setting up databases using docker images:
  
## MongoDB:
  
Creating Mongo database from docker image

* #### Pull the latest mongodb image:
  
```
docker pull mongo
```

* #### Create the mongodb container and publish port 27017:
  
```
docker run -d -p 27017:27017 --name <container_name> mongo
```
  
* #### Create the mongodb container, publish port 27017, and persist the data created:
  
```
docker run -d -p 27017:27017 -v data-vol:/data/db --name <container_name> mongo
```
* #### Accessing the mongodb shell in the container:
  
```
docker exec -it <container_name> bash
```
