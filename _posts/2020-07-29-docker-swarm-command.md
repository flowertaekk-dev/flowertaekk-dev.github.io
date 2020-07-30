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

### Node Clustering에서 Node란?

* Docker swarm에서 Cluster를 구성하는 물리적 또는 논리적으로 분리 된 독립적인 서버를 의미 

#### $ docker node

* `$ docker node` 명령어는 해당 서버를 swarm에 등록하거나 등록해제하는 역할!
  * 또한, node의 권한(manager/worker) 설정도 가능하게 한다.

### Manager란?

* 하나의 Cluster를 관리하는 매니저!

### Overlay란?

* Swarm-wide bridge network driver where containers can communicate across nodes!

#### $ docker network create --driver overlay (network name)

### Routing Mesh

* 들어오는 Packet을 자동으로 로드밸런싱 하는 건가? (공부 필요)
  * [여기에 자세히 설명되어 있다](https://www.udemy.com/course/docker-mastery/learn/lecture/6790710#overview)

#### Routing Mesh 특징

* Stateless load balancing
* This Load balancer is at OSI Layer 3 (TCP)
* 위의 문제 때문에 하나의 cluster에서 두 개 이상의 웹 서비스를 운영하려면 곤란하다.
  * 이문제는 nginx 등을 이용한 proxy를 이용함으로써 해결 가능! (하다고 한다)
    * 아직 감이 잘 안 오지만 한 번 만들어보면 감이 오려나

* *감이 왔다갔다한다... 좀 더 알아보자* 

### Swarm으로 cluster 구축하기 위한 port 설정

* TCP port 2377 for cluster management communications
* TCP and UDP port 7946 for communication among nodes
* UDP port 4789 for overlay network traffic

[참고](https://docs.docker.com/engine/swarm/swarm-tutorial/#open-protocols-and-ports-between-the-hosts)

## Command

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

[참고](https://stackoverflow.com/questions/38602903/docker-swarm-init-could-not-choose-an-ip-address-error)

### $ docker node ls

* `docker swarm init` 으로 생성한 node 확인

### $ docker service

* service in a Swarm replaces `docker run`
  * service 명령어를 통해 cluster를 구성하는 node들에 일괄적으로 명령을 실행시킬 수 있다.

#### $ docker service ls

* REPLICAS 항목
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

### $ docker swarm join-token manager

* manager용 swarm 토큰을 발행받는다.
  * 이 token으로 worker에게 매니저 권한을 부여할 수 있다.

### $ docker swarm join-token worker

* worker용 swarm 토근.
  * 이걸 이용해서 cluster 에 worker를 추가할 수 있다.

### $ docker node update --role manager (node name)

* worker 노드를 manager 노드로 승진시킬 수 있다!
