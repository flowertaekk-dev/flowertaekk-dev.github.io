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
    * Servers + Change Rate = Benefit of orchestration.
* It enables for us to control lots of servers at once.

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
  * master node 들의 집합이라고 보면 될 듯!
* *Pod* : One or more containers running together on one Node
* Controller: For creating/updating pods and other objects
* Service: Network endpoint to connect to a pod
* etcd: Distributed storage system -> DB
  * 발음은 엣씨디..

### About Service

#### ClusterIP

* cluster 내에서 사용되는 IP

#### NodePort

* 다른 노드 또는 외부에서 접근할 수 있는 IP

#### LoadBalancer

* cluster로 통하는 LB의 endpoint를 관리.
* Only availabel when infra provider gives us a LB (AWS's ELB... etc..)

### Node Structure

#### Master

* etcd
* API
* Scheduler
* Controller manager
* Core DNS

#### Node (worker)

* kublet (agent)
* kube-proxy : controls network

### Local setup

* MicroK8s : ubuntu 버전으로 나왔지만 다른 OS에서도 잘 작동함. 

#### 1.

{% highlight cmd %}
$ snap microk8s --classic --channel=1.18/stable
{% endhighlight %}

#### 2.

{% highlight cmd %}
$ microk8s.enable dns
{% endhighlight %}

참고: `microk8s.xxx` 명령어로 다양한 조작 가능!

##### Tips

`alias kubectl=microk8s.kubectl` 설정해놓는걸 추천`

### kubectl 가동 방법

#### `kubectl run`

* `kubectl run` only create single pods.
    * ex) `$ kubectl run <Pods name> --image <image name>`

#### `kubectl create`

* creates replicaSet
    * ex) `$ kubectl create <Deployment> <Pods> --image <image name>`

#### `kubectl apply`

* yml 하고 같이 사용됨.

### Command

#### `$ kubectl get pod`

* List of pods
* `-w` option can be used. (--watch)

#### `$ kubectl get all`

* List of all objects on different layers

#### `$ kubectl delete <replicaSet, pod> <pod name>`

* Delete Pod

#### `$ kubectl scale <replicaSet name> <pod name> --replicas <num>`

* Update the number of replicas
* It is the same as `4 kubectl scale deployment (node name) --replicas <num>`
* `kubectl scale <short name replicaSets>/<pod name> --replicas <num>`
    * ex) kubectl scale deploy/my-httpd --replicas <num>
        * deploy = deployment = deployments

#### `$ kubectl logs deploy/(pod name)`

* option
    * --follow: works like -f option with tail
        * ex) `kubectl logs deploy/my-apache --follow --tail 1`
* 컨테이너 내부 로그 확인
* 많은 pod를 가지고 있더라도 하나만 가지고 와서 보여준다. 첫 라인에서 확인 가능.

#### `$ kubectl describe <resource type> <pod name>`

* It is very simliar to `inspect` command in docker
* 자세한 로그 확인 가능. 컨테이너 사양에 대해서도 확인 가능.

#### `$ kubectl expose deployment/<pod name> --port <port number>`

* To open port.
* Create clusterIP
  * expost command로 서비스를 생성하는 것!
  * clusterIP는 내부에서만 접속 가능하다! host OS 에서는 안 되는게 정상!
    * Linux host에서는 가능!
  * curl 등으로 확인하려면 새로운 pod를 생성해서 bash로 들어간 후에 curl을 날릴 수 있다.
    * service name이 DNS가 되기 때문에 `curl my-httpd:(port)`로 쓸 수 있다.
* ex) `kubectl expose deploy/(node name) --port (port num) --name (alias) --type NodePort`
* ex) `kubectl expose deploy/(node name) --port (port num) --name (alias) --type LoadBalancer`

#### NodePort 서비스 추가하기

* `$ kubectl expose <resource name>/<pods name> --port <port number> --name <nodePort name> --type NodePort`

* `$ kubectl get service` 를 해보면 추가되는걸 알 수 있는데 포트가 0000:30000 형식으로 되어있다. 
    * <cluster IP>:<외부에 노출되는 IP> 

#### LoadBalancer 서비스 추가하기

* `$ kubectl expose <resource name>/<pods>name> --port <port number> --name <loadBalancer name> --type LoadBalancer`
