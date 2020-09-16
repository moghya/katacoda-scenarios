We have been creating and running multiple containers.
Container takes disk space and even after the container has stopped, occupied space remains as is. It's better to remove these containers.

`clear`{{execute}}

`docker rm --help`{{execute}}

`docker ps -a`{{execute}}

Run command `docker rm container_ids`

While running container, flag `--rm` can be specified to ensure that container gets cleaned after it exits.