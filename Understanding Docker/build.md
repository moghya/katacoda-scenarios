Let's build docker image of a simple web application.

`ls -al`{{execute}}

`clear`{{execute}}

For this we'll clone following tweet app hosted on github.  
`git clone https://github.com/dockersamples/linux_tweet_app`{{execute}}

`ls -al linux_tweet_app`{{execute}}

We can see that there is a `Dockerfile` in this project.

`cat linux_tweet_app/Dockerfile`{{execute}}

    # Using FROM instruction it is specified to use NGINX as the base image.
    FROM nginx:latest
    
    # using COPY instruction, files are copied to directory that nginx servers files.
    COPY index.html /usr/share/nginx/html
    COPY linux.png /usr/share/nginx/html

    # Using EXPOSE instruction it is specified that the process that this container created from this image would listen on ports 80 and 443.
    EXPOSE 80 443

    # Using CMD instruction, default way of executing this container is specifed.
    CMD ["nginx", "-g", "daemon off;"]

That's pretty easy to understand, ain't it?
Let's build it and run it.

`docker build -t linux_tweet_app .`{{execute}}

`docker container run --d -p 80:80 linux_tweet_app`{{execute}}  

## Push docker image to DockerHub:

`clear`{{execute}}

`docker login`{{execute}}

`docker push yourusername/linux_tweet_app`

`docker run -p 5555:80 yourusername/linux_tweet_app`

## Exercise:
`Modify Dockerfile, rebuild image and run it:`
1. Use ARG instruction to accpet a string.
2. Add header tag in `index.html` file with header tag's text to be same as accepted string.
3. Post modification copy the `index.html` to nginx.
4. Build docker image.
5. Run this image with introduced `ARG` parameter.
6. Push this image to DockerHub.
