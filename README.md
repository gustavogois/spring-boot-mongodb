# spring-boot-mongodb
This repository contains a Spring Boot example project for MongoDB.

For a code review of this repo, see my related [blog post](https://springframework.guru/3402-2/).

You can learn more about my courses [here](http://courses.springframework.guru/courses/) on my site.

## Run the application

```mvn spring-boot:run```

## Docker Commands

- ```docker run -p 27017:27017 -d mongo```

- ```docker run -p 27017:27017 -v /Users/gustavogois/projetos/spring-boot-mongodb/dockerdata/mongo:/data/db -d mongo```

- ```docker logs -f 2d829b113cbd```
- ```docker logs 91094e7def43```

## Other useful commands

- ```lsof -nP -i4TCP:8080 | grep LISTEN```

- ```kill -9 <<pid>>```

- ```history | grep mongo```
- ```!577```