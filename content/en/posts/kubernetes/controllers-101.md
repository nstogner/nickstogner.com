---
title: 'Kubernetes Controllers 101'
description: Short introduction to Kubernetes controllers
date: 2024-07-11T08:02:09-04:00
draft: false
tags:
  - kubernetes
  - controllers
image: /images/kubernetes-controllers-101.png
---

![Kubernetes Controllers 101](/images/kubernetes-controllers-101.png)

Kubernetes controllers are processes that watch objects in the Kubernetes API Server and adjust the state of a target system (like a container or load balancer) to match the desired state declared by those objects.

Controllers keep a long-running GET request to the API Server held open. The API Server streams any changed objects on this connection. Controllers then compare the desired state (usually originating from a YAML manifest file) with the actual state of the target system. If changes are needed, controllers will issue commands to the system (like starting a container or updating a load balancer). The current state is often reported back to the user via updates to the object's `.status` field.

Note: For some controllers the target system is the API Server itself. For example, the ReplicaSet controller is responsible for ensuring a desired number of Pod replicas exist in the API Server.
