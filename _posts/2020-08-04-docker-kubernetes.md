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

### Local setup

#### 1.

{% highlight cmd %}
$ snap microk8s --classic --channel=1.18/stable
{% endhighlight %}

#### 2.

{% highlight cmd %}
$ microk8s.enable dns
{% endhighlight %}


