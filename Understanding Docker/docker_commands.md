
## List running containers:

Now that we know that docker can be used to create, run and manage containers.
Let's see what all containers are running currently.

`docker ps --help`{{execute}}

`docker ps`{{execute}}

`docker ps -a`{{execute}}

Ah, we don't have any containers. Well it makes sense because we did not create and run any. We need `image` for creating `container`.

## List images:

Let's see what images are available with us.

`docker images --help`{{execute}}

`docker images`{{execute}}


We don't even have any images. We need to get images from `DockerHub`.

DockerHub is a registry that maintains well built docker images for development and distribution.

Fundamentally Registry is a web server hosting images files that can be downloaded locally using docker tool.These images are to be used for creating containers.

## Pull docker images from registry

Let's pull some `image` and create container.

`docker pull --help`{{execute}}


`hello-world` image is created and maintained by `Docker`.

This image has a binary that prints `Hello World` message.

It is suggested to pull and run this image to verify that the docker is installed and running properly.

`docker pull hello-world`{{execute}}

## Create and run Container by using Image: