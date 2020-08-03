---
title: "Docker basics"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - basics
toc: true
---

## Docker Basics

### Docker's networking structure

* [27. Docker Networks: Concepts for Private and Public Comms
in Containers](https://www.udemy.com/course/docker-mastery/learn/lecture/6758364#overview)
  * docker 네트워크 구조에 대해 그림으로 설명해준다.

### Docker Image naming convention

user/repo:tag

* official image에는 user가 생략된다.

## Dockerfile

* FROM (image name)
* ENV (variable name) (value)
* WORKDIR (path)
* RUN (command)
* EXPOSE (port...)
* CMD ["command"]

### Dockerfile의 기본 네이밍은 Dockerfile

* 다른 이름으로 만들수도 있다. 다만 실행할 때는 `-f` 옵션과 함께 사용.

### Persistent Data: Bind Mounting

* Maps a host file or directory to a container file or directory
* Mounting된 볼륨은 실시간 동기화된다.

## Docker Compose

### 사용하는 이유

* Configure relationships between containers

### Docker Compose는 두가지로 구성된다.

1. YAML-formatted file that describes our solution options for
  * containers
  * networks
  * volumes
2. A CLI tool `docker-compose` used for local dev/test automation with those YAML files.

### Docker Compose file naming convention

* docker-compose.yml is default filename but any can be used with `docker-compose -f`

## Docker Healthchecks

* HEALTHCHECK is supported in DOckerfile, Compose YAML, docker run, and Swarm Services.
* It is running inside of our container, so we can healthcheck a container that has not a exposed port.
* exit 0 (OK)
* exit 1 (Error)
* Three container states: starting, healthy, unhealthy

### To do Healthcheck

* need to add option to Dockerfile like:
  * `HEALTHCHECK curl -f http://localhost/ || false`

{% highlight cmd  %}
HEALTHCHECK --timeout=2s --interval=3s --retries=3 \
  CMD curl -f http://localhost/ || exit 1
{% endhighlight  %}
