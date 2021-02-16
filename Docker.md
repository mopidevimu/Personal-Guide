# Docker UserGuide

## What is Docker
<p>Docker is a set of platform as a service products that use OS-level
virtualization to deliver software in packages called containers. 
Containers are isolated from one another and bundle their own software,
libraries and configuration files they can communicate with each other
through well-defined channels.</p>

## What is Docker Image
- The actual package or application.
- Artifact that can be moved around.

## What is Docker Container
- Container is actually made of Images or Layers of Images (package or application).
- Mostly Linux base Image, Because small in size.
- Container is a running environment for Image.
- Port Binded, to talk with applications running inside of container.

## Basic Docker Commands
- Pulling an image from Docker-hub public repository.
```
docker pull <image name>
Example:
 docker pull python 
```

- Pulling an Image with required version of that specific Image.
```
docker pull <image name:version>
Example: 
docker pull python:3.10.0a5-alpine3.12 
```

- Pulling latest version of Image
```
docker pull <image-name:latest>
Example:
 docker pull python:latest
```

- Starting or running an Docker Image.
```
docker run <image-name>
Example: 
docker run python
```
<p> NOTE: If you want to directly pull and run that image same time, you can direcly use the above command "docker run <image-name>". once you run this command it checks that image available locally otherwise it will automatically pull that image and run same time. </p>

- Running an Docker image in detach mode.
```
docker run <image-name> -d
Example: 
docker run python -d
```
<p>NOTE: The above command will run the conatiner in command line and it detach from that command line.</p>

- Checking running docker containers
```
docker ps
```
<p>NOTE: The above command will list down all the running contianers(images) with "CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES".</p>

- If currently no container is running but you want to check history of docker containers which are stopped.
```
docker ps -a
```
<p>NOTE: The above command will list down all the running contianers(images) with "CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES".</p>

- Stopping docker container
```
docker stop <Contianer-Id>
Example: 
docker stop 898246e1d8d2
```
<p>NOTE: How do we know contianer id.? by runniner "docker ps" command we can get the docker container Id.</p>

- Running a two different versions of same Image with different PORT address to communicate with them.

Example you are installed two versions of Mysql.
```
-- mysql:latest
-- mysql:5.7.33
```
<p>Once run those images and check with "docker ps", you  will notice both of them having same PORT address. If they are having same port address we cannot communicate with them or unreachable. So we can change their post addresses.</p>
 
Example PORT address 
```
-- mysql:5.7.33 is 8379/tcp
-- mysql:latest is 8379/tcp
```
We can change those port address using following command.
```
docker run -p8000:8379 mysql:latest

open new terminal or cmd

docker run -p8001:8379 mysql:5.7.33

-------------------OR-------------------

docker run -d -p8000:8379 mysql:latest

docker run -d -p8001:8379 mysql:5.7.33
```
<p>NOTE: Now you can check with "docker ps" command to find the PORT address the containers are changed or not. So, now we can use them with latest ports.</p>

- If you want to change the Image names of a container.
```
docker run -d -p8001:8379 --name mysql-older mysql:5.7.33 

docker run -d -p8000:8379 --name mysql-new mysql:latest
```
<p>NOTE: you can check the modifications using "docker ps" </p>

- If you want to check logs of container.
```
docker logs <image name>
Example:
docker logs mysql:5.7.33
-------------------OR--------------
If you changed the name of image.
docker logs  mysql-older
```

- If you want to OPEN TERMINAL of running container.
```
docker exec -it <Container-Id or name or image>
Example:
docker exec -it  898246e1d8d2 /bn/bash
```
<p> The above command will open the container as root user in bash mode in same terminal. you can EXIT that termianl by using "exit".</p>
<p>NOTE: How do we know contianer id.? by runniner "docker ps" command we can get the docker container Id.</p>

- If you want to check docker images which are installed in your system.
```
docker images
```
<p>NOTE: The above command will list down all the images which are existed in system.</p>

## Advanced Docker Commands

- If you want to check existed docker networks or create network.

-- List down all existed networks by defalut.
```
docker networks ls
```

-- Creating a New own Network
```
docker networks create <network-name>
Example:
docker networks create MyNetwork
```

- If you want to remove Docker container
-- Force-remove a running container
```
docker rm --force <container name>
Example:
docker rm --force mysql
```
--Remove a container and its volumes
```
docker rm -v <container name>
Example:
docker rm -v mysql
```

--Remove a container and selectively remove volumes
```
Example volume : docker create -v awesome:/foo -v /bar --name hello mysql

docker rm -v hello
```

-- Remove all stopped containers
```
docker rm $(docker ps -a -q)
```

- Showing disk usage by container
```
docker ps -s
```

- If you want to restart a container
```
docker restart mysql
```

