---
layout: base
title: Documentation
---

## Overview
Clocker adds container support for Apache Brooklyn. It currently comes with various entities to be able to deploy to [Docker Swarms](https://docs.docker.com/swarm/){:target="blank"} and [Kubernetes clusters](http://kubernetes.io/){:target="blank"}

The way it works is as follow:

1. Use Brooklyn to deploy one of the container platforms into clouds. This deployment will effectively become a Brooklyn location.
2. Use Brooklyn to deploy apps onto those newly deployed container plateforms

In short, your container platforms *and* your applications are deployed *and* managed through a central and common interface, **Apache Brooklyn**.  And Brooklyn gives you a UI, a CLI, a REST API, and policy support to manage them all in a consistent way.

## Entities available
There is further documentation for each type of container that Clocker supports:

* [Docker Swarm](swarm-cluster.html)
* [Kubernetes cluster](kubernetes-cluster.html)
