---
title: 'Kueue 101'
date: 2024-07-25T14:32:01-04:00
draft: false
tags:
  - kubernetes
  - controllers
  - hpc
---

![Kueue 101](/images/kueue-101.png)

Kueue is a [Kubernetes controller](../controllers-101) that helps control access to scarce compute resources. These resources might be highly sought-after GPUs in the cloud or limited on-premise CPU nodes. Kueue decides when a batch workload should run by keeping track of what is running, comparing that to the total available resource capacity, and taking into account a set of ordering criteria.

To understand Kueue's place in the Kubernetes ecosystem it is useful to consider what would happen without it. Consider a large multi-tenant cluster used for training ML models. What would happen if there were more training Jobs submitted than there were GPUs to run on? In this case, the Kubernetes scheduler would attempt to assign as many Pods to Nodes as possible, disregarding aspects such as who submitted their Jobs first or which users/teams were already hogging most of the resources. With Kueue, administrators are able to [declaratively configure rules](https://kueue.sigs.k8s.io/docs/concepts/cluster_queue/) to bring order and fairness to the cluster.

Note: Kueue has more functionality than can be discussed in this short intro post. For example: Kueue actually supports an assortment of workloads (not just `kind: Job`). If you are interested in learning more check out the [official website](https://kueue.sigs.k8s.io/).
