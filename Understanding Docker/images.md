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