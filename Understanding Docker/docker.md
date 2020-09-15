    an open-source project that automates the deployment of software applications inside containers by providing an additional layer of abstraction and automation of OS-level virtualization on Linux.

- Docker is a tool that allows developers, sys-admins etc. to easily deploy their applications in a sandbox (called containers) to run on the host operating system i.e. Linux. The key benefit of Docker is that it allows users to package an application with all of its dependencies into a standardized unit for software development.

It means docker is a full fledged tool that helps in creating and manaing containers and hence helping solve the problems that we intend to solve.

`docker info`{{execute}}

`docker version`{{execute}}

## How are containers created using Docker:
A `container` is launched by running an `image`.

An image is an executable package that includes everything needed to run an application--the code, a runtime, libraries, environment variables, and configuration files.
