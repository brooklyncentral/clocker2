---
layout: base
title: Swarm Cluster Features
---

### Docker Swarm configuration
The Docker Swarm blueprint comes with built-in configuration that allows you to control how your Docker Swarm will be deployed and manage.

#### Auto scaling
There is auto-scaling functionality included with a deployed Swarm cluster by default. There is currently no option to scale down. There are some configuration options that control how the scale is performed:

| Config Name             | Description                                                                                           |
|-------------------------|-------------------------------------------------------------------------------------------------------|
| swarm.initial.size      | The initial number of swarm nodes to create                                                           |
| swarm.max.size          | The maximum number of swarm nodes to scale up to                                                      |
| swarm.scaling.cpu.limit | The percentage limit at which we should scale up. This should be a double value between 0.00 and 1.00 |
| swarm.manager.size      | The number of swarm managers                                                                              |


#### Networking
The Swarm cluster is automatically setup with an overlay network. This network can be used by containers deployed to the swarm cluster to communicate. There are some configuration options that control networking:

| Config Name          | Description                                                                                  |
|----------------------|----------------------------------------------------------------------------------------------|
| swarm.defaultnetwork | The ID of the default network to set. When deploying to this swarm, this network can be used |
| swarm.discovery.url  | URL of a provided discovery mechanism for the swarm                                          |
| swarm.port           | The TCP port the Swarm manager listens on                                                    |

#### Hardware
The Swarm nodes can be provisioned on with specific hardware requirements. There are some configuration options that control what machines are provisioned:

| Config Name    | Description                                    |
|----------------|------------------------------------------------|
| swarm.minCores | Minimum CPU cores for provisioning Swarm nodes |
| swarm.minRam   | Minimum RAM for provisioning Swarm nodes       |