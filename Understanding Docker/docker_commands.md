
## List Containers:

Now that we know that docker can be used to create, run and manage containers.
Let's see what all containers are running currently.

`clear`{{execute}}

`docker ps --help`{{execute}}

`docker ps`{{execute}}

`docker ps -a`{{execute}}

Ah, we don't have any containers. Well it makes sense because we did not create and run any. We need `image` for creating `container`.

## List Images:

Let's see what images are available with us.

`clear`{{execute}}

`docker images --help`{{execute}}

`docker images`{{execute}}

That's nice. We have a couple of Images avaiable locally.

`hello-world` is a imagecreated and maintained by `Docker`.
It has a binary that prints `Hello World` message.

It is suggested to pull and run `hello-world` image to verify that the docker is installed and running properly. We need to get images from `DockerHub`.

DockerHub is a registry that maintains well built docker images for development and distribution.

Fundamentally, Registry is a web server hosting image files that can be downloaded locally using docker tool. These images are to be used for creating containers.

## Pull Docker Image:

Let's pull some `hello-world` image.

`clear`{{execute}}

`docker pull --help`{{execute}}

`docker pull hello-world`{{execute}}

`docker images`{{execute}}

Now we can see that `hello-world` image is pulled from DockerHub.

## Create Container from Image:

Now that we have the image let's create a Container.

`clear`{{execute}}

`docker create --help`{{execute}}

`docker create --name first-hello-world hello-world`{{execute}}

`docker ps -a`{{execute}}

## Start the Container:

Now that we have created a container let's start it.

`clear`{{execute}}

`docker start --help`{{execute}}

`docker start first-hello-world -a`{{execute}}

`docker ps -a`{{execute}}

Do you notice the `COMMAND` column in result of above command. It shows the program that was invoked in the created container.
Container stops once the invoked program stops. In this case it's 
`/hello`. It's a simple binary which is printing the message that we see. 

In practice this command will be the one invoking the application that user intends to run in container.

## Run Container:

There are multiple ways of starting a container.

`clear`{{execute}}

`docker run --help`{{execute}}

`docker run hello-world`{{execute}}

`run` command creates and starts the container.  
It evens goes on to pull image, if it is not found locally.

`docker ps -a`{{execute}}

`hello-world` image does not have anything more that we can explore. 

Let's try playing with another image named `busybox`. 
This image has the `busybox` binary which provides several Unix utilities in a single executable file.

`clear`{{execute}}

Notice that we never pulled busybox and straight away we're trying to run it. Also we're passing a command. This command will be executed from within the container.

`docker run busybox  echo "hello there from busybox"`{{execute}}

`docker ps -a`{{execute}}

The passed command executed and container stopped. If we want to invoke multiple commands in container we need to run it in interactive mode.

Let's do that now.

`clear`{{execute}}

Notice the `it` flag that we're passing in below command. It runs the container in interactive mode and essentially attaches the `STDIN` 

`docker run -it busybox sh`{{execute}}

Run any commands that you could run on shell.

Now one should wonder if this is actually a container and run commands that would make it evident.

Participants are requested to share any innovative approaches.

## Remove Container:

We have been creating and running multiple containers.
Container takes disk space and even after the container has stopped, occupied space remains as is. It's better to remove these containers.

`clear`{{execute}}

`docker rm --help`{{execute}}

`docker ps -a`{{execute}}

Run command `docker rm container_ids`

## Containers involving network services:

`clear`{{execute}}

So far the images that we have explored are basic ones. None of them did have any major application in them.

Let's try to pull an image having a Static Website Application packaged into it. We'll run this application from within the container and see how docker/continer technology handles the network port aspect of the web server process.

Let's first understand the below command.

`-d` flag runs container in detached mode. Thius container is going to run a webserver process. It has to keep running and as we want to go ahead have it run in backgroun we use `-d` flag.

`-P` flag publishes all exposed ports to random ports. Essentially what happens is all the ports exposed by process in container are mapped to randome ports on our local machine. As the process is a web server it would be listening for requests on some port.

`--name` flag as explained earlier gives name to this container.

Let's execute the command.

`docker run -d -P --name first-static-site dockersamples/static-site`{{execute}}

Post execution we can check what all ports have been exposed by this container and what is the mapping.

`docker port --help`{{execute}}

`docker port first-static-site`{{execute}}

Now use the KataCoda UI and open exposed ports to visit page served by webserver runnning from container.

