# Docker Basics

## Terms
 - Client/server architecture
 - Containers
 - Dockerfiles
 - Docker daemon (engine)
 - Docker registries
 - Hypervisors 
 - Images
 - Kernel
 - Process
 - Virtual machines

## Summary
 - Docker is a platform for consistently building, running, and shipping applications
 - Using hypervisors we can create and manage virtual machines. The most popular hypervisors are VirtualBox, VMware and Hyper-v (Windows-only)
 - Docker uses client/server architecture.
 - It has a client component that talks to the server using a RESTful API.
 - The server is also called the Docker engine (or daemon) runs in the background and is responsible for doing the actual work
 - Using Docker, we can bundle an application into an image. Once we have an image, we can run it on any machine that runs Docker.
 - To bundle an application into an image, we need to create a Dockerfile.
 - A Dockerfile contains all the instructions needed to package up an application into an image
 - We can share our images by publishing them on Docker registries.
 - The most popular Docker registry is Docker Hub

# Images
## Dockerfile instructions
```
FROM            # to specify the base image 
WORKDIR         # to set the working directory
COPY            # to copy files/directories
ADD             # to copy files/directories
RUN             # to run commands 
ENV             # to set environment variables
EXPOSE          # to document the port the container is listening on
USER            # to set the user running the app
CMD             # to set the default command/program
ENTRYPOINT      # to set the default command/program
```
## Image commands
```
docker build -t <name> .
docker images 
docker image ls 
docker run -it <image> sh
```
## Example Dockerfile for building image for Spring boot java application
```

FROM maven:3.8.6 AS build
WORKDIR /app
COPY pom.xml /app
RUN mvn dependency:resolve
COPY . /app
RUN mvn clean
RUN mvn package -DskipTests


FROM openjdk:17-jdk-alpine
COPY --from=build /app/target/*.jar app.jar

EXPOSE 9090
CMD ["java","-jar","app.jar"]

```
## Example Building mysql image using docker-compose.yml
```
version: '3.1'

services:
  ecommerce:
    image: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 'password'
    ports:
      - "3309:3306"
    volumes:
      - ./data.sql:/docker-entrypoint-intidb.d/data.sql
```
# Containers
## Running containers
```
docker run <image>
docker run -d <image>                       # run in the background
docker run —name <name> <image>             # to give a custom name 
docker run —p 3000:3000 <image>             # to publish a port HOST:CONTAINER
```
## Listing containers
```
docker ps                  # to list running containers
docker ps -a               # to list all containers
````

## Viewing the logs
```
docker logs <containerID>
docker logs -f <containerID> # to follow the log
docker logs —t <containerID> # to add timestamps
docker logs —n 10 <containerID> # to view the last 10 lines
```

## Executing commands in running containers
```
docker exec <containerID> <cmd>
docker exec -it <containerID> sh # to start a shell
```

## Starting and stopping containers
```
docker stop <containerID> 
docker start <containerID>
````
## Removing containers
```
docker container rm <containerID> 
docker rm <containerID> 
docker rm -f <containerID>            # to force the removal
docker container prune               # to remove stopped containers
```
## Volumes
```
docker volume ls
docker volume create app-data
docker volume inspect app-data
docker run -v app-data:/app/data <image>
```
## Copying files between the host and containers
```
docker cp <containerID>:/app/log.txt .
docker cp secret.txt <containerID>:/app
````
## Copying files between the host and containers
```
docker run -v $(pwd):/app <image>
```
