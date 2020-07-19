---
title: "Docker command"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - command
toc: true
---

## Docker Command

### docker command line structure

* old(still work) : docker (command) (options)
* new: docker (command) (sub-commnad) (options)

### $ docker version

* Version 확인
* Client 버전과 Server버전을 확인할 수 있다.

### $ docker info

* Check information for installed docker more than `$docker version`

### $ docker

* Can check basic Docker command with this command

### $ docker container run

* starts a new container from an image
* run 명령어는 새로운 container를 생성한다! (start와 차이점)

* What happends when we run this command?
  1. Looks for that image locally in image cache.
  2. If cannot find anything, then looks in remote image repository (by default DockerHub)
  3. Downloads the latest version (nginx:latest by default)
  4. Creates new container based on that image and prepares to start
  5. Gives it a virtual IP on a private network inside docker engine
  6. Opens up port 80 on host and forwards to port 80 in container
  7. Starts container by using the CMD in the image Dockerfile

{% highlight cmd %}
$ docker container run --publish 80:80 nginx

1. Downloads image 'nginx' from DockerHub
2. Starts a new container from that image
3. Opens port 80 on the host IP ( --publish 80 )
4. Rouths that traffic to the container IP : ( 80 )

{% endhighlight %}

#### --detach

{% highlight cmd %}
$ docker container run --publish 80:80 --detach nginx
{% endhighlight %}

* `--detach` 는 docker를 백그라운드에서 돌아가도록 하는 명령어

#### --name (container name)

* 새로 생성되는 컨테이너의 이름을 설정할 수 있다.

### $ docker container ls

* 현재 실행 중인 container list 보기

#### -a

* 모든 container list 보기

### $ docker container stop (container ID)

* 실행 중인 container 종료하기

### $ docker container logs (container name)

* 특정 컨테이너의 로그 보기

### $ docker container top (container name)

* 특정 컨테이너 안에서 돌아가고 있는 프로세스 확인

### $ docker container rm (container ID ...)

* container 제거하기

#### -f

* 실행 중인 컨테이너도 강제로 종료하고 제거한다.
