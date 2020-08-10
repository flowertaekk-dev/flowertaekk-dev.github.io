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

### Service Types

1. ClusterIP (default)
  * It is only good in the cluster. REMEMBER THIS!
2. NodePort
  * Port to connect to outside of cluster.
3. LoadBalancer
  * Controls a LB endpoint external to the cluster.
4. ExternalName
  * Adds CNAME DNS record to CoreDNS only.
  * Not used for Pods, but for giving ods a DNS name to use for somthing outside Kubernetes
  * Not used that many.

### Imperative vs. Declarative

* Imperative: Focus on how a program operates
  * We care of every single process
* Declarative Focus on what a program should accomplish
  * We don't care process, but we just want it to run!

#### Imperative

* Ex) kubectl run, kubectl create deployment, kubectl update
* Imperative is easier when you know the state
* Imperative is easier to get started
* Imperative is easier for humans at the CLI
* Imperative is NOT easy to automate

#### Declarative

* Ex) kubectl apply -f prac.yaml
* Same command each time
* Resources can be all in a file, or many files
  * *The point is that everything works with yaml file*
* More work than kubectl run for just starting a pod
* The easiest way to automate

### GitOps

* Kubernetes 를 이용해서 배포를 선언적으로 한다는 의미라는데 공부가 필요!!!!

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

#### `$ kubectl expose deployment/(pod name) --port (port number)`

* To open port.
* Create clusterIP
  * clusterIP는 내부에서만 접속 가능하다! host OS 에서는 안 되는게 정상!
    * Linux host에서는 가능!
  * curl 등으로 확인하려면 새로운 pod를 생성해서 bash로 들어간 후에 curl을 날릴 수 있다.
    * service name이 DNS가 되기 때문에 `curl my-httpd:(port)`로 쓸 수 있다.
* ex) `kubectl expose deploy/(node name) --port (port num) --name (alias) --type NodePort`
* ex) `kubectl expose deploy/(node name) --port (port num) --name (alias) --type LoadBalancer`

#### `$ kubectl delete service/(service name)`

* Delete service from kubernetes
