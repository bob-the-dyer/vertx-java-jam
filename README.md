    Microservices with Vertical Flying-off (MVF) with vert.x 

The goal is to show how to use vert.x to develop, deploy and maintain micro-services.
To build project use: mvn clean package

Verticals are deployed as a fat jar in both "native"(via vertx launcher) and embedded (inside spring boot app) 
modes inside Docker containers. 
To build project, deploy and run microservices in Docker use: mvn clean package -P con,run
 - con profile - creates Docker image
 - run profile - run Docker image 
To build all containers at once use: sh buildall.sh
To run all containers at once use: docker-compose up

    Plan for speech
 - Who am I
 - Intro: why vert.x
 - Producer: exploring groovy code, maven build, Dockerfile, deployment to docker
 - Consumer: exploring ruby code, maven build, Dockerfile, deployment to docker
 - web: exploring js client and server code, maven build, Dockerfile, deployment to docker, test in browser
 - Start mongo in docker
 - Persistor: exploring java code, maven build, Dockerfile, deployment to docker
 - Resume 
 
    Bonus topics
- https://www.techempower.com/benchmarks/
- HA, quorum
- vert.x internals: event loop, worker pool, shared data, nio
        

    Negative things to mention
 - hazelcast by default has timeouts and delays that should be configured for each particular case.    
 - rmi host of docker machine for boot2docker needs to be specified -Djava.rmi.server.hostname='192.168.99.100', on linux and native MAC set it to 0.0.0.0 

    Hints for docker interaction:
 - To initialize docker environment run in terminal: eval "$(docker-machine env default)"
 - Docker bridge network is 172.17.0.X
 - Docker machine address for boot2docker is 192.168.99.100
 - To kill all containers at once use: docker kill $(docker ps -q)
 - To remove all containters at once use:
    1. docker stop $(docker ps -a -q)
    2. docker rm $(docker ps -a -q)
 - To remove all none images use: docker rmi $(docker images | grep "^<none>" | awk "{print $3}")
 - To run mongodb in docker container use: docker run -it --rm --name joker-mongo -p 27017:27017 mongo
 - To remove all images use:
    1.docker rm $(docker ps -a -q) 
    2.docker rmi $(docker images -q)
 
     Hints for docker-compose interaction: 
 - docker-compose up -d
 - docker-compose ps
 - docker-compose stop
 - docker-compose up
 - docker-compose scale producer=5