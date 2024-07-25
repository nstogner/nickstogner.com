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

Kueue is a [Kubernetes controller](../controllers-101) that helps control access to scarce compute resources. These resources might be highly sought-after GPUs in the cloud or limited on-premise CPU nodes. Kueue decides when a Job should run by keeping track of what is running and comparing that to a configured resource capacity.

To understand Kueue's place in the Kubernetes ecosystem it is useful to consider what would happen without it. Consider a large multi-tenant cluster used for training ML models. What would happen if there were more Jobs submitted than there were resources? In this case, the Kubernetes scheduler would attempt to assign as many Pods to Nodes as possible, disregarding aspects such as who submitted their Jobs first or which users/teams were already hogging most of the resources. With Kueue, administrators are able to declaratively configure rules to bring order and fairness to the cluster.

Note: Kueue can support multiple types of [workloads](https://kueue.sigs.k8s.io/docs/concepts/workload/), not just Jobs. If you are interested in learning more check out the [official website](https://kueue.sigs.k8s.io/).
