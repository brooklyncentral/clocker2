---
layout: base
title: Swarm Cluster Features
---

### Overview
This page contains an overview of a number of Container Service features.

#### Auto scaling
There is auto-scaling functionality included with a deployed Swarm cluster by default. There is currently no option to scale down. There are some configuration options that control how the scale is performed:

| Config Name             | Description                                                                                           |
|-------------------------|-------------------------------------------------------------------------------------------------------|
| swarm.initial.size      | The initial number of swarm nodes to create                                                           |
| swarm.max.size          | The maximum number of swarm nodes to scale up to                                                      |
| swarm.scaling.cpu.limit | The percentage limit at which we should scale up. This should be a double value between 0.00 and 1.00 |


#### Networking
The Swarm cluster is automatically setup with an overlay network. This network can be used by containers deployed to the swarm cluster to communicate. There are some configuration options that control networking:

| Config Name          | Description                                                                                  |
|----------------------|----------------------------------------------------------------------------------------------|
| swarm.defaultnetwork | The ID of the default network to set. When deploying to this swarm, this network can be used |
