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

### docker-compose can use `$ docker secret`??

* No! It just works as though there is docker swarm database and use its secret database.
  * docker-compose는 production용이 아니라는 사실을 기억하자! develop 용일뿐!
  * docker-compose가 이런 기능을 제공함으로써 우리는 개발 중에도 production 모드의 스크립트를 그대로 사용할 수 있다는 이점을 가져갈 수 있다!

{% highlight yml%}
version: "3.1"

services:
  psql:
    image: postgres
    secrets:
      - psql_user
      - psql_password
    environment:
      POSTGRES_PASSWORD_FILE: /run/secrets/psql_password
      POSTGRES_USER_FILE: /run/secrets/psql_user

secrets:
  psql_user:
    file: ./psql_user.txt
  psql_password:
    file: ./psql_password.txt
{% endhighlight %}
