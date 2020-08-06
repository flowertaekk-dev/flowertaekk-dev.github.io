---
title: "Docker Kubernetes"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - Kubernetes
toc: true
---

## Docker Kubernetes

* Kubernets is a popular container orchestrator
* Container Orchestration is something that makes many servers act like one.

### What is the benifit of using orchestration?

* It automatically applies changes. (Is it the most important benefit??)
* It enables for us to control lots of servers at once.

### Advantages of Swarm

* Easy to manage
* Comes with Docker
* Runs anywhere Docker does
* Secure by default
* Easier to troubleshoot

### Advantages of Kubernetes

* a bit difficult(?) but more functional
* Clouds will deploy/manage Kubernetes for us
* Widest adoption and community
* Trendy

### Terms

* Kubernetes: The whole orchestration system. Also called as K8s
* Kubectl: CLI to configure Kubernetes and manage apps
* Node: Single server in the Kubernetes cluster
* Kubelet: Kubernetes agent running on nodes(workers)
* Control Plane: Similar to Manager in Swarm but it also means group of masters
  * Sometimes it is called as master
* Pod: One or more containers running together on one Node
* Controller: For creating/updating pods and other objects
* Service: Network endpoint to connect to a pod

### Local setup

#### 1.

{% highlight cmd %}
$ snap microk8s --classic --channel=1.18/stable
{% endhighlight %}

#### 2.

{% highlight cmd %}
$ microk8s.enable dns
{% endhighlight %}

### Command

#### There are 3 ways to create pods from the kubectl CLI!

1. `$ kubectl run` : similiar to `$ docker run`
  * ex) `$ kubectl run my-nginx --image nginx`
2. `$ kubectl create` : similiar to `$ docker swarm`
  * ex) `$ kubectl create deployment my-nginx --image nginx`
3. `$ kubectl apply` : similiar to `$ docker stack`


#### `$ kubectl get pod`

* List of pods
* `-w` option can be used. (--watch)

#### `$ kubectl get all`

* List of all objects on different layers

#### `$ kubectl delete pod (pod name)`

* Delete Pod

#### `$ kubectl scale deploy/(node name) --replicas (num)`

* Update the number of replicas
* It is the same as `4 kubectl scale deployment (node name) --replicas (num)`

#### `$ kubectl logs deploy/(pod name)`

* option
  * --follow: works like -f option with tail

#### `$ kubectl describe pod (pod name)`

* It is very simliar to `inspect` command in docker

