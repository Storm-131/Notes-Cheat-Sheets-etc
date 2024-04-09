# Docker 🐳

## 🌵 Basics

```bash
# Show Version
docker -v    # Check the current version
docker info  # Get even more information

# List all images
docker images                          # list all images
docker image rm <image_name>           # remove an image
docker build <path> --tag <image_name> # build image from dockerfile

# List running containers
docker ps        # list running containers
docker ps -a     # list running and stopped containers
```

```bash
# Pull an image
docker pull <image_name>     # Pull an image from a server

# Run container from image
docker run -d <image_name>    	 # Every time it creates a new container
docker start id                  # Start container again

docker stop $(docker ps -aq)     # stop all containers
docker rm -f $(docker ps -a -q)  # remove all containers

docker run -p <host_port>:<container_port> # map host port to container
docker run -v <host_directory>:<container_directory> # mount host
docker run -env <key>=<value>   # pass environment variable

# Run additional command in existing / currently running container
docker dontainer exec -it <image> bash   

# Give details of a container
docker inspect <container_id>

# Saving and Loading
docker save predector/predector > predector.tar  # Save an Image
docker load < predector.tar                      # Load an Image
```

```bash
# Compose
docker-compose build    # builds images
docker-compose up       # starts containers
docker-compose stop     # stops running containers
docker-compose rm       # removes stopped containers
```

---

### Cleaning Up

```bash
# Stop
docker container stop <name/ID>             # Stop the image
docker container stop $(docker ps -a -q)    # Stops all containers

# Remove
docker container rm <name/ID>  # Remove the Container; First letters of ID are enough; -f to force deletion
docker container rm $(docker ps -a -q)  # Removes all stopped containers
docker rmi $(docker images -a -q) # Remove all images

# Prune
docker system prune #|Remove all unused images, containers, etc.
```

---

### Inside the Container

Mounting the host system into a container allows the container to read and write to the host system.

```bash
# Processes
docker container top 		# Process list in one container
docker container inspect	# Details of one container config (Metadata)
docker container stats	   # Performance stats for all containers (live-CPU, etc.)
docker container logs	    # View the logs of a container

# Host-Mounting
docker run -v <HOST_DIRECTORY>:<CONTAINER_DIRECTORY>
docker run it -v $(pwd):/mounted ubuntu:14.04 /bin/bash	# Mounting a host-folder inside a docker-image

#--> Example;
#  "$(pwd)" is the path to our current directory
# ":/mounted" is the folder in the container

exit 	# Leaves the current running Terminal inside the container
```

---

## 🌵 Conda in Docker

```bash
# 1) Download image
docker pull continuumio/miniconda3

# 2) Run interactive shell
docker run -i -t continuumio/miniconda3 /bin/bash
docker run -i -t bio-code /bin/bash

# - With connected volume on host
docker run -i -t -v /path/on/host:/path/inside/container <image_name>

# 3) Save customized container to image
docker ps -a
sudo docker commit [CONTAINER_ID] [new_image_name]
sudo docker commit ...

# 4) Copy and load the image
docker save image_name > image_name.tar
docker load -i <path to image tar file>

# Push repo
docker push ...
```

---

### Installing the autocompletion

https://docs.docker.com/docker-for-mac/#install-shell-completion

```bash
Install homebrew
Install autocompletion-tool

# Add a line in your bash.profile
[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion

# Create links:
ln -s /Applications/Docker.app/Contents/Resources/etc/docker.bash-completion /usr/local/etc/bash_completion.d/docker
ln -s /Applications/Docker.app/Contents/Resources/etc/docker-machine.bash-completion /usr/local/etc/bash_completion.d/docker-machine
ln -s /Applications/Docker.app/Contents/Resources/etc/docker-compose.bash-completion /usr/local/etc/bash_completion.d/docker-compose
```

---

### Tutorials

1. [Nana's Techworld](https://www.youtube.com/watch?v=3c-iBn73dDE)
2. [Understanding Docker (as GameBoy)](https://medium.com/@audretschjames/understanding-docker-as-if-it-were-a-gameboy-96c96392efbf)
3. [Udemy-Course](https://www.udemy.com/course/docker-mastery/)

---
