So far we have been learning how to use existing image to create containers and then manage the created containers.

It's time we :
- build our own docker image.
- create container using the built image
- push image to docker hub
- pull image created by other participants and try running containers


Before that let's first understand a bit about docker architechture:

## Docker components:

- Docker Daemon :
  - The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.

- Docker Client:
  - The command line tool that allows the user to interact with the daemon. More generally, there can be other forms of clients too - such as Kitematic which provide a GUI to the users.

- Docker Hub:
  - A registry of Docker images. If required, one can host their own Docker registries and can use them for pulling images. (Private/OnPrem registries)

## How to build Docker Image - Dockerfile:
