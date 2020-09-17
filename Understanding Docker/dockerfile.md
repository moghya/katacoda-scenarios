So far we have been learning how to use existing image to create containers and then manage the created containers.

It's time we :
- build our own docker image.
- create container using the built image
- push image to docker hub
- pull image created by other participants and try running containers

## How to build Docker Image - Dockerfile:

A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image.

`docker build --help`{{execute}}

The docker build command builds an image from a `Dockerfile` and a context. 
The build’s context is the set of files at a specified location `PATH` or `URL`. The `PATH` is a directory on your local filesystem. The `URL` is a Git repository location.

`Dockerfile` supports certain instructions.
Let's understand all possible instructions and how to use them. Post that we'll go ahead and create our own docker file.

- `FROM`   
  A `Dockerfile` must begin with a `FROM` as in must be the first non-comment instruction in the Dockerfile. The `FROM` instruction specifies the Parent/Base Image for building image in question.
  - `FROM <image>`
  - `FROM <image>:<tag>`
  - `FROM <image>@<digest>`


- `MAINTAINER`  
  The `MAINTAINER` instruction allows us to set the Author field of the generated images.
  - `MAINTAINER <name>`

- `RUN`:   
  The `RUN` instruction will execute any commands in a new layer on top of the current image and commit the results. The resulting committed image will be used for the next step in the Dockerfile
  - `RUN <command>` (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
  - `RUN ["<executable>", "<param1>", "<param2>"]` (exec form)

- `CMD`:   
  Purpose of a `CMD` is to provide defaults for an executing container.
  - `CMD ["<executable>","<param1>","<param2>"]` (exec form, this is the preferred form)
  - `CMD ["<param1>","<param2>"]` (as default parameters to ENTRYPOINT)
  - `CMD <command> <param1> <param2>` (shell form)

- `LABEL`:   
  The LABEL instruction adds metadata to an image.
  - `LABEL <key>=<value> [<key>=<value> ...]`

- `EXPOSE`:   
  Informs Docker that the container listens on the specified network port(s) at runtime.
  - `EXPOSE <port> [<port> ...]`

- `ENV`:   
  The `ENV` instruction sets the environment variable `<key>` to the value `<value>`.
  - `ENV <key> <value>`
  - `ENV <key>=<value> [<key>=<value> ...]`

- `ADD`:   
  Copies new files, directories, or remote file URLs from `<src>` and adds them to the filesystem of the image at the path `<dest>`.
  `<src>` may contain wildcards and matching will be done using Go’s filepath.Match rules.
  If `<src>` is a file or directory, then they must be relative to the source directory that is being built (the context of the build).
  `<dest>` is an absolute path, or a path relative to `WORKDIR`.
  If `<dest>` doesn’t exist, it is created along with all missing directories in its path.
  - `ADD <src> [<src> ...] <dest>`
  - `ADD ["<src>", ... "<dest>"]` (this form is required for paths containing whitespace)

- `COPY`:   
  `COPY` takes in a src and destination. It only lets you copy in a local file or directory from your host (the machine building the Docker image) into the Docker image itself.
  `COPY <src> [<src> ...] <dest>`
  `COPY ["<src>", ... "<dest>"]` (this form is required for paths containing whitespace)

- `ENTRYPOINT`:   
  Allows user to configure a container that will run as an executable.
  Command line arguments to docker run `<image>` will be appended after all elements in an exec form `ENTRYPOINT` and will override all elements specified using `CMD`.
  The shell form prevents any `CMD` or run command line arguments from being used, but the `ENTRYPOINT` will start via the shell. This means the executable will not be PID 1 nor will it receive UNIX signals. Prepend exec to get around this drawback.
  Only the last `ENTRYPOINT` instruction in the Dockerfile will have an effect.
  `ENTRYPOINT ["<executable>", "<param1>", "<param2>"]` (exec form, preferred)
  `ENTRYPOINT <command> <param1> <param2>` (shell form)

- `USER`:   
  The `USER` instruction sets the user name or `UID` to use when running the image and for any `RUN`, `CMD` and `ENTRYPOINT` instructions that follow it in the Dockerfile.
  - `USER <username | UID>`

- `WORKDIR`:   
  Sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions that follow it.
  It can be used multiple times in the one Dockerfile. If a relative path is provided, it will be relative to the path of the previous `WORKDIR` instruction.
  - `WORKDIR </path/to/workdir>`

- `ARG`:   
  Defines a variable that users can pass at build-time to the builder with the docker build command using the `--build-arg <varname>=<value>` flag.
  Multiple variables may be defined by specifying ARG multiple times.
  - `ARG <name>[=<default value>]`

- `ONBUILD`:   
  Adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build. The trigger will be executed in the context of the downstream build, as if it had been inserted immediately after the `FROM` instruction in the downstream Dockerfile.
  Any build instruction can be registered as a trigger.
  Triggers are inherited by the "child" build only. In other words, they are not inherited by "grand-children" builds.
  The `ONBUILD` instruction may not trigger `FROM`, `MAINTAINER`, or `ONBUILD` instructions.
  - `ONBUILD <Dockerfile INSTRUCTION>`

- `STOPSIGNAL`:   
  The STOPSIGNAL instruction sets the system call signal that will be sent to the container to exit. This signal can be a valid unsigned number that matches a position in the kernel’s syscall table, for instance 9, or a signal name in the format `SIGNAME`, for instance `SIGKILL`.
  - `STOPSIGNAL <signal>`

- `HEALTHCHECK`:   
  Tells Docker how to test a container to check that it is still working
  Whenever a health check passes, it becomes healthy. After a certain number of consecutive failures, it becomes unhealthy.
  - `HEALTHCHECK [<options>] CMD <command>` (check container health by running a command inside the container)
  - `HEALTHCHECK NONE` (disable any healthcheck inherited from the base image)
  The `<options>` that can appear are...
  `--interval=<duration>` (default: 30s)
  `--timeout=<duration>` (default: 30s)
  `--retries=<number>` (default: 3)


- `SHELL`:   
  Allows the default shell used for the shell form of commands to be overridden.
  Each SHELL instruction overrides all previous SHELL instructions, and affects all subsequent instructions.
  Allows an alternate shell be used such as zsh, csh, tcsh, powershell, and others.
  - `SHELL ["<executable>", "<param1>", "<param2>"]`
