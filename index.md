---
layout: website-normal
title: Swarm cluster for Clocker 2
children:
- swarm_cluster_features.md
- tutorial/index.md
---

## What is it?

Clocker 2 for [Apache Brooklyn](https://brooklyn.apache.org/) is a set of open source, [Apache Licensed](https://www.apache.org/licenses/LICENSE-2.0) tools designed to make working with [Docker](https://www.docker.com/) containers as simple as a few clicks. Clocker 2 contains [Brooklyn blueprints](http://brooklyn.apache.org/v/latest/start/blueprints.html) to enable deployment and management of [Docker Swarms](https://www.docker.com/products/docker-swarm) and [Kubernetes clusters](http://kubernetes.io/).

## What can you do with it?

* You can easily deploy production grade Docker Swarms or Kubernetes clusters to a [range of clouds](http://brooklyn.apache.org/v/latest/ops/locations/index.html).
* You can manage and scale Swarms or clusters in real time. 

## Getting started
Firstly, you need to have [Apache Brooklyn installed](https://brooklyn.apache.org/v/latest/start/running.html). Once this is done, [download the `clocker2-common.bom` file](c  locker2-common.bom). This file contains all required entities to run a Docker Swarm cluster. You need to add this file to your Brooklyn catalog. You can achieve this by either drag-and-dropping the file into the YAML editor (composer tab of the Brooklyn UI) or by using the [Brooklyn CLI](https://brooklyn.apache.org/v/latest/ops/cli/index.html) as follow:

    br add-catalog clocker2-common.bom

Then you need to [setup a location](https://brooklyn.apache.org/v/latest/ops/locations/index.html) to deploy your Docker Swarm cluster. We came up with location's templates to add to your catalog, that you can use out of the box for [AWS](tutorial/locations/aws-example-location.bom), [SoftLayer]((tutorial/locations/sl-example-location.bom)), [Azure](tutorial/locations/azure-example-location.bom), [GCE](tutorial/locations/gce-example-location.bom) and [Blue Box](tutorial/locations/bb-example-location.bom). You can find more information about what is going on in those files [here](tutorial/swarmCluster.html#setup-a-cloud-location).

Now you are all set. The last thing to do is to deploy your Docker Swarm cluster. You can use this [yaml](examples/swarm.yaml){:target="blank"} to getting started:
{% highlight YAML %}
{% include_relative examples/swarm.yaml %}
{% endhighlight %}
