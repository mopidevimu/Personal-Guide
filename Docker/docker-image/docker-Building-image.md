## Creating a basic image

# Creating an image that runs redis-server usi g existing base image alpine of redis

Step-1 
    - Create a Folder for an image.
      
      Example: redis-image 

Step-2
    - Create a file called Dockerfile uisng the following below code.
      
      Dockerfile

      ```docker
      -- Use an Existinfg docner image as a base
            FROM alpine

      -- Download and isntall a dependency
            RUN apk add --update redis
      -- Tell the image what to do when it starts 

      -- As a container
            CMD ["redis-server"]
      ```

Step-3
    - Run a command on terminal (open terminal inside redis folder)
      ```docker
      docker build .
      ```

Step-4
    - Once the image build successfully, run the following command.
      ```docker
      docker run <build image id>
      ```