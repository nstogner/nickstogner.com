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

To understand Kueue's place in the Kubernetes ecosystem it is useful to consider what would happen without Kueue. Consider the case where there are more Jobs submitted into a multi-tenant cluster than there are resources. In this case, the Kubernetes scheduler would attempt to assign as many Pods to Nodes as possible, disregarding concepts such as who submitted their Jobs first or what users are currently hogging most of the resources on the cluster. With Kueue, administrators are able to declaratively configure rules to bring order and fairness to the cluster.

Note: Kueue can support multiple types of [workloads](https://kueue.sigs.k8s.io/docs/concepts/workload/), not just Jobs. If you are interested in learning more check out the [official website](https://kueue.sigs.k8s.io/).
