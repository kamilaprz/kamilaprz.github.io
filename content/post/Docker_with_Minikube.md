---
title: "Docker with Minikube and Testcontainers"
description: "After Dockers' subscription plan has changed, many are looking for an alternative solution, to run their containers while on MacOs. Minikube is definitely an option to consider, to spin up Linux VM and run containers in."
tags: ["mac", "docker", "minikube", "container", "docker desktop", "testcontainers"]
date: 2022-07-25T07:52:44+02:00
draft: true
---

# Docker subscription model

Docker has changed its [subscription](https://www.docker.com/blog/updating-product-subscriptions/) plan and Docker Desktop is not free for large organisations anymore. 
Docker Engine works on Linux as a daemon and makes it possible to run docker containers on top of Linux kernel. Docker Desktop, however, is not a core Docker technology, but it makes it easier to spin up Docker containers on Mac and Windows machines, it actually spins up Linux VM which is used for running containers.

Since the subscription model was changed, one can either keep an old version of Docker Desktop (and not have to accept new terms of use and subscription plan) or remove Docker Desktop and go for an alternative solution. I picked the second option.
To remove Docker Desktop click a bug icon and then click Uninstall.

### Linux VM environment
To run Docker containers without Docker Desktop on Mac, one would have to set up Linux VM. One option to consider here, can be Minikube. To install Minikube with bower, type in a terminal

```
brew install hyperkit
brew install minikube
```

Setup Minikube with Docker:
```
eval $(minikube docker-env)
# mind sudo here:
echo "`minikube ip` docker.local" | sudo tee -a /etc/hosts > /dev/null
```

### Testcontainers

Now, Docker will use Minikube to start containers. The only thing left in the setup, is to tell testcontainers how to use Minikube setup.
To do so, run the following commands in the terminal:

```
echo "docker.host=$DOCKER_HOST" >> ~/.testcontainers.properties
echo "docker.cert.path=$DOCKER_CERT_PATH" >> ~/.testcontainers.properties
echo "docker.tls.verify=true" >> ~/.testcontainers.properties
```