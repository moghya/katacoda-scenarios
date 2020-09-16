Now that we have created a container let's start it.

`clear`{{execute}}

`docker start --help`{{execute}}

`docker start first-hello-world -a`{{execute}}

`docker ps -a`{{execute}}

Do you notice the `COMMAND` column in result of above command. It shows the program that was invoked in the created container.
Container stops once the invoked program stops. In this case it's 
`/hello`. It's a simple binary which is printing the message that we see. 

In practice this command will be the one invoking the application that user intends to run in container.