---
title: 'Kubernetes Controllers 101'
date: 2024-07-11T08:02:09-04:00
draft: false
tags:
  - kubernetes
  - controllers
---

![Kubernetes Controllers 101](/images/kubernetes-controllers-101.png)

Kubernetes controllers are processes that watch objects in the Kubernetes API Server and adjust the state of a target system (like a container or load balancer) to match the desired state declared by those objects.

Controllers keep a long-running GET request to the API Server is held open, streaming any object changes. They compare the desired state (usually originating from a YAML manifest file) with the actual state of the target system. If changes are needed, controllers will issue commands to the system (like starting a container or updating a load balancer) and often update the object's `.status` field.

For some controllers the target system is the API Server itself. For example, the ReplicaSet controller is responsible for ensuring a desired number of Pod replicas exist in the API Server.
