# spring-boot-mongodb
This repository contains a Spring Boot example project for MongoDB.

For a code review of this repo, see my related [blog post](https://springframework.guru/3402-2/).

You can learn more about my courses [here](http://courses.springframework.guru/courses/) on my site.

## See the logs and running the app

The Mongo's container is running in the background. To see the logs of this container:

```
docker logs -f <container_id>
```

Run the application:

```mvn spring-boot:run```

### Notes

- We're no overriding any properties at all (application.property is empty). We're purely using the spring boot defaults. 
- We're not using the embedded MongoDB.

## Images X Container

- In an analogy, docker images are like java's class, while the container represents the instances of the images.
- An Image defines a Docker container.
- Images are immutable. Once built, the files making up an image do not change.
- Images are built in layers. Each layer is an immutable file (but is a collection of files and directories)
- Layers receive an ID. Thus, if the layer contents change, the ID changes too.

### Notes

- Command to see the mongo's image:

```
docker image inspect mongo
```

- Command to see complet hash ID

```
docker images -q --no-trunc
```

## Docker Commands

- ```docker run -p 27017:27017 -d mongo```

- ```docker run -p 27017:27017 -v /Users/gustavogois/projetos/spring-boot-mongodb/dockerdata/mongo:/data/db -d mongo```

- ```docker kill 749d087e19d9```

- ```docker logs -f 2d829b113cbd```
- ```docker logs 91094e7def43```

## Rabbit MQ

- ```docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 rabbitmq:3-management```

## MYSQL

- ```docker run --name gois-mysql2 -v /Users/gustavogois/projetos/spring-boot-mongodb/dockerdata/mysql:/var/lib/mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -p 3306:3306 -d mysql```

## Some concepts

- "With a lot of Docker containers, you're going to be setting environment variables, mapping ports, and mapping storage."

## House Keeping

- There are 3 key areas of house keeping: containers, images and volumes

### Containers

- Kill all running Docker containers: ```docker kill $(docker ps -q)```
- Delete all Stopped Docker Containers: ```docker rm $(docker ps -a -q)```

### Images

- Remove a Docker Image: ```docker rmi <image name>```
- Delete Untagged (dangling) images: ```docker rmi $(docker images -q -f dangling=true)```
- Delete All Images: ```docker rmi $(docker images -q)```

### Volumes

- Once a volume is no longer associated with a container, it's considered 'dangling'
    - Remove all dangling volumes: ```docker volume rm $(docker volume ls -f dangling=true -q)```
    - Note: Does not remove files from host system in shared volumes

https://springframework.guru/docker-cheat-sheet-for-spring-devlopers/ 

## Other useful commands

- ```lsof -nP -i4TCP:8080 | grep LISTEN```
- ```sudo lsof -iTCP -sTCP:LISTEN -n -P```

- ```kill -9 <<pid>>```

- ```history | grep mongo```
- ```!577```

- ```ls -tlr```

