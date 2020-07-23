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
