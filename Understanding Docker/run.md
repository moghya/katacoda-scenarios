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