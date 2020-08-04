---
title: "Docker service"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - docker
  - service
toc: true
---

## Docker service

### `$ docker service update`

* scale, rollback, health check 기능도 있다.

#### To update with new image

{% highlight cmd  %}
$ docker service update --image (image name) (service name)
{% endhighlight  %}

##### It should work as the same as:

{% highlight cmd  %}
$ docker stack deploy -c (docker-compose.yml file) (stack name)
{% endhighlight  %}

#### To add an environment variable

{% highlight cmd  %}
$ docker servie update --env-add (variable name)=(value)
{% endhighlight  %}

#### To add a port to a service being used

{% highlight cmd  %}
$ docker servie update --publish-add (port number):(container port)
{% endhighlight  %}

#### To remove a port being used

{% highlight cmd  %}
$ docker servie update --publish-rm (port number)
{% endhighlight  %}

#### To rebalance tasks across nodes

{% highlight cmd  %}
$ docker servie update --force (service name)
{% endhighlight  %}

### `$ docker service scale`

{% highlight cmd  %}
$ docker servie scale (service name)=(the number of replicas) (service name)=(the number of replicas)
{% endhighlight  %}
