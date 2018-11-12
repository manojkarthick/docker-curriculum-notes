## Docker curriculum notes/cheatsheet

This notes contains the important terms and commands from the Docker curriculum beginners tutorial. Content is copy-pasta from [Docker curriculum](https://docker-curriculum.com/). All mistakes are mine.


To run the basic docker + to check installation: `docker run hello-world`. Runs the hello-world docker, can be used to check the installation.

Glossary

Terminology | Explanation
----------- | -----------
Images | The blueprints of our application which form the basis of containers. In the demo above, we used the docker pull command to download the busybox image.
Containers | Created from Docker images and run the actual application. We create a container using docker run which we did using the busybox image that we downloaded. A list of running containers can be seen using the docker ps command.
Docker Daemon | The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system to which clients talk to.
Docker Client | The command line tool that allows the user to interact with the daemon. More generally, there can be other forms of clients too - such as Kitematic which provide a GUI to the users.	
Docker Hub | A registry of Docker images. You can think of the registry as a directory of all available Docker images. If required, one can host their own Docker registries and can use them for pulling images.
Image Tag | Snapshot of the docker image
Base images | images that have no parent image, usually images with an OS like ubuntu, busybox or debian
Child images | images that build on base images and add additional functionality
Official images | images that are officially maintained and supported by the folks at Docker
User images | images created and shared by users, formatted as `user/image-name`
onbuild images | Images that include ONBUILD triggers, will COPY a requirements.txt file, pip install the file, copy the current directory into /usr/src/app.
Dockerfile | contains commands that the Docker client runs while creating an image


Commands:

Purpose | Command | Notes
------- | ------- | -----
Get an image from Docker registry | `docker pull <image-name>` | With tag: `docker pull <image-name>:<tag>`
List of all images on local machine | `docker images`
To run a particular command on a docker container | `docker run <image> command` | Just running docker run for an image will run a container with empty command and shut down. The run command keeps the container alive only as long as the command is running.
Get list of docker containers running | `docker ps`
Get list of docker containers running + exited | `docker ps -a`
Open interactive shell inside docker | `docker run -it <imagename> sh`
Remove a docker from local | `docker rm <container-id>`
Removing all containers that have exited | `docker rm $(docker ps -a -q -f status=exited)` | `docker container prune` also does the same; -a shows all; -q shows IDs only; -f filters with `status=exited`
Pull image + Remove when exits + run | `docker run --rm <imagename>`
See exposed ports of running container | `docker port <container-name>`
Stop detached container | `docker stop <container-name>`
Search registry | `docker search <query>`
Build an image from dockerfile | `docker build -t <optional-tag> <directory-of-dockerfile>`
Publish to Registry | `docker push <imagename>`


Docker Run flags

Flag | Use
---- | ---
-i | interactive
-t | allocate pseudo-tty
--rm | remove container when exiting
-d | detached mode
-P | publish all exposed ports to random ports
-p | local:exposed
--name | name of container

**IMPORTANT**: `docker run` flags are order sensitive

Dockerfile commands

Command | Use
------- | ----
FROM | Specify base image
EXPOSE | Port to be exposed
CMD | Command to run when starting the container











