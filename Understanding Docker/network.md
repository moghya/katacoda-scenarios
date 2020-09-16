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

It would be better to specify port mappings while running container with network services.

`-p` flag can be used to set port mapping for a container.

`docker run -d -p 80:80 --name second-static-site dockersamples/static-site`{{execute}}