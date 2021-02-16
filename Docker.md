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
Example: docker pull python 
```

- Pulling an Image with required version of that specific Image.
```
docker pull <image name:version>
Example: docker pull python:3.10.0a5-alpine3.12 
```

- Pulling latest version of Image
```
docker pull <image-name:latest>
Example: docker pull python:latest
```

- Starting or running an Dacoker image
```
docker run <image-name>
Example: docker run python

<p> NOTE: If you want to directly pull and run that image same time, you can direcly use the above command "docker run <image-name>". once you run this command it checks that image available locally otherwise it will automatically pull that image and run same time. </p>
```

- Running an Dacoker image in detach mode
```
docker run <image-name> -d
Example: docker run python -d

NOTE: The above command will run the conatiner in command line and it detach from that command line.
```

- Checking running docker containers
```
docker ps

NOTE: The above command will list down all the running contianers(images) with "CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES".
```

- If currently no container is running but you want to check history of docker containers which are stopped.
```
docker ps -a

NOTE: The above command will list down all the running contianers(images) with "CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES".
```

- Stopping docker container
```
docker stop <Contianer-Id>
Example: docker stop 898246e1d8d2

NOTE: How do we know contianer id.? by runniner "docker ps" command we can get the docker container Id.
```

- Running a two different versions of same Image with different PORT address to communicate with them.
```
Example you are installed two versions of Python
-- mysql:5.7.33
-- mysql:latest

Once run those images and check with "docker ps", you  will notice both of them having same PORT address. If they are having same port address we cannot communicate with them or unreachable. So we can change their post address.
 
 Example PORT address 
-- mysql:5.7.33 is 8379/tcp
-- mysql:latest is 8379/tcp

