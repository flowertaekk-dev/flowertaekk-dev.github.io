---
title: "docker-swarm command"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - swarm
  - command
toc: true
---

## Swarm

* Swarm은 Manager와 Worker로 구분해서 하나의 매니저가 요구사항을 Worker들에게 공유함으로써 여러 Worker들을 한 번에 관리할 수 있는 방식인듯?!
  * 하나 하나 관리하지 않고 여러 Worker들을 일괄적으로 관리!

### $ docker info

* `$ docker info` 를 통해 Swarm이 active 상태인지 inactive상태인지 알 수 있다.
  * Swarm: inactive

### $ docker swarm init

* `$ docker swarm init` 역할
  * Root Signing Certificate created for our Swarm
  * Certificate is issued for first Manager node
  * Join tokens are created

#### docker swarm init 에러

{% highlight cmd  %}
Error response from daemon: could not choose an IP address to advertise since this system has multiple addresses on interface
{% endhighlight %}

#### docker swarm init 에러 대응

{% highlight cmd  %}
docker swarm init --advertise-addr=(Physical IP)
{% endhighlight %}

1. `ifconfig` 로 Physical IP 주소 찾기 
2. 위에 있는 코드 실행

[참고]:(https://stackoverflow.com/questions/38602903/docker-swarm-init-could-not-choose-an-ip-address-error)

### $ docker node ls

* `docker swarm init` 으로 생성한 node 확인

### $ docker service

* service in a Swarm replaces `docker run`

#### $ docker service ls

* REPLICAS
  * (the number of active container)/(the number of container we specified)

#### $ docker service update (ID) --replicas (number)

* To scale up, can use this command

#### $ docker service ps (service name)

* Can also check ps history

#### $ docker service rm (service name)

* remove service

### $ docker update

* Can set or change variables without stop or kill the active docker container
* *It is not Swarm command*
  * For Swarm, use `docker service update` command


