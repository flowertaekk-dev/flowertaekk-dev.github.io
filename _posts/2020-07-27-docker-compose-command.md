---
title: "docker-compose command"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - docker-compose
  - command
toc: true
---

## docker-compose command

It is not a production-grade tool but ideal for local development and test.

### Most common command

#### $ docker-compose up

* Setup volumes/networks and start all containers according to docker-compose.yml file

#### $ docker-compose down

* Stop all containers and remove containers, volumes, and networks

### docker-compose.yml file looks like:

{% highlight yml %}
version: '3.1'  # if no version is specified then v1 is assumed. Recommend v2 minimum

services:  # containers. same as docker run
  servicename: # a friendly name. this is also DNS name inside network
    image: # Optional if you use build:
    command: # Optional, replace the default CMD specified by the image
    environment: # Optional, same as -e in docker run
    volumes: # Optional, same as -v in docker run
    ports: # Optional, same as -p in docker run
  servicename2:

volumes: # Optional, same as docker volume create

networks: # Optional, same as docker network create
{% endhighlight  %}

### Using Compose to Build

* Compose will bulid images with `docker-compose up` if image not found in cache
* Can rebuild with `docker-compose build` command

#### $ docker-compose build
