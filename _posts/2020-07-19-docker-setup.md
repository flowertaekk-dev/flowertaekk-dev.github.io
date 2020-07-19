---
title: "Docker setup"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - setup
toc: true
---

## Docker setup

### sudo 없이 docker command 사용 가능하도록 하기

{% highlight cmd  %}
$ sudo usermod -aG docker <group명>
{% endhighlight  %}

보안이 신경쓰이면 이 옵션은 쓰지 않는 편이 좋을수도.
Fedora, RedHat 등에서는 이 옵션 안 먹힌다.

#### Hint

Docker는 root하고만 통신이 가능한 구조(?)

### Docker Machine & Docker Compose

#### 1. docker-machine

[Docker Machine installation](https://docs.docker.com/machine/install-machine/)

{% highlight cmd  %}
$ docker-machine version
{% endhighlight  %}

#### 2. docker-compose

[Docker Compose installation](https://docs.docker.com/compose/install/)
[gitHub에서도 받을 수 있다](https://github.com/docker/compose/releases)

{% highlight cmd  %}
$ sudo -i
$ chmod +x /usr/local/bin/docker-compose ## 권한 설정이 필요
$ docker-compose version
{% endhighlight  %}

