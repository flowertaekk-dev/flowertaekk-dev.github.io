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

## Docker Basic Command

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

#### --rm

* 컨테이너 실행 종료와 동시에 컨테이너를 제거한다.

#### --detach

{% highlight cmd %}
$ docker container run --publish 80:80 --detach nginx
{% endhighlight %}

* `--detach` 는 docker를 백그라운드에서 돌아가도록 하는 명령어

#### --name (container name)

* 새로 생성되는 컨테이너의 이름을 설정할 수 있다.

#### -v

* Named volume 이라고 부른다.
  * 그냥 컨테이너를 생성하면, 어느 volume이 해당 컨테이너의 볼륨이지 알아보기가 힘들기 때문에 이름을 지정해서 volume을 생성하도록 할 수 있다.

{% highlight cmd %}
$ docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v (volume name):/var/lib/mysql mysql
## /var/lib/mysql 은 mysql의 default mount point다.
{% endhighlight %}

* Bind Mounting

{% highlight cmd %}
$ docker container run -v (absolute path in host):(path to container)
{% endhighlight %}



#### --env (-e)

* 생성되는 컨테이너에 환경변수를 전달할 때 사용 된다.

{% highlight cmd %}
$ docker container run --p 3306:3306 -d -e MYSQL_RANDOM_ROOT_PASSWORD=true  nginx
{% endhighlight %}

#### --network (network name)

* 사용할 네트워크를 지정할 수 있다.

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

### $ docker ps

* docker에서 실행 중인 프로세스 확인

### $ docker container top

* List running processes in specific container

### $ docker container inspect

* details of one container config
* show metadata about the continaer (startup config, volumes, networking, etc)

#### --format

* A common option for formatting the output of commands using "Go templates"

{% highlight cmd %}
$ docker container inspect --format '{{ .NetworkSettings.IPAddress  }}' (container name)
{% endhighlight %}

### $ docker container stats

* performance stats for all containers
* show live performance data for all containers

### $ docker container run -it

* start new container interactively
  * container 안으로 들어가서 커맨드 조작이 가능할 수 있도록
* What is the `-it` option?
  1. `-t` : simulates a real terminal, like what SSH does
    * pseudo-TTY
  2. `-i` : keep session open to receive terminal input

### $ docker container exec -it

* run additional command in existing container

{% highlight cmd %}
$ docker container exec -it (container name) (command)
$ docker container exec -it mysql bash
{% endhighlight %}

### $ docker container start 

* 기존 컨테이너를 실행한다

#### -ai

* 기존 컨테이너를 실행하고, 컨테이너로 접속한다.

### $ docker container port (container name)

* Can check port configuration

## Docker Networks

### $ docker network ls

* Show networks

### $ docker network inspect (network name)

* Inspect a network

### $ docker network create --driver

* Create a network

### $ docker network connect (network name) (container name)

* Attach a network to container
* Dynamically creates a NIC in a container on an existing virtual network
  * NIC: Network Interface Card

### $ docker network disconnect (network name) (container name)

* Detach a network from container

## DockerHub

### $ docker pull (image name)

* DockerHub 로부터 이미지를 다운받는다.

{% highlight cmd %}
$ docker pull nginx:(version number)
{% endhighlight %}

### $ docker image push

* uploads changed layers to a image registry

### $ docker login

* ~/.docker/config.json 에 로그인 정보가 기록되기 때문에 공유컴퓨터에서 로그인 한 경우에는 반드시 `$ docker logout` 할 것.

### $ docker logout

## Images

### $ docker image history (image name)

* Show image history

### $ docker image inspect (image name)

* Return JSON metadata about the image

### $ docker image tag SOURCE_IMGAE[:TAG] TARGET_IMAGE[:TAG]

* Create new tag name

### $ docker image build -t (tag) (path)

* To build with Dockerfile

## Docker System

### $ docker system df

* docker가 사용중인 메모리의 내역을 보여줌

### $ docker system prune

* docker system에 있는 모든 것들을 초기상태만 남기고 제거함.
* docker system prune보다 하나하나씩 지정해서 삭제하는 것이 더 안전하다. (아래처럼)

#### $ docker image prune
#### $ docker container prune
#### $ docker volume prune

## Volumn

### $ docker volume create 

It is required to do this before `$ docker run` to use custom drivers and labels
