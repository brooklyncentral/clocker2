---
layout: website-normal
title: Swarm cluster for Clocker 2
children:
- swarm_cluster_features.md
- tutorial/index.md
---

## What is it?
The Docker Swarm cluster for Clocker 2 is a set of YAML blueprints designed to make Docker more accessible to deploy application from [Apache Brooklyn](https://brooklyn.apache.org/).

## What can you do with it?
* You can easily create and manage a production grade Docker Swarm cluster.
* It allows you to deploy your apps to Docker Swarm clusters, allowing you to seamlessly blend Docker with more traditional deployments.

## Getting started
Firstly, you need to have [Apache Brooklyn installed](https://brooklyn.apache.org/v/latest/start/running.html). Once this is done, [download the `clocker2-common.bom` file](c  locker2-common.bom). This file contains all required entities to run a Docker Swarm cluster. You need to add this file to your Brooklyn catalog. You can achieve this by either drag-and-dropping the file into the YAML editor (composer tab of the Brooklyn UI) or by using the [Brooklyn CLI](https://brooklyn.apache.org/v/latest/ops/cli/index.html) as follow:

    br add-catalog clocker2-common.bom

Then you need to [setup a location](https://brooklyn.apache.org/v/latest/ops/locations/index.html) to deploy your Docker Swarm cluster. We came up with location's templates to add to your catalog, that you can use out of the box for [AWS](tutorial/locations/aws-example-location.bom), [SoftLayer]((tutorial/locations/sl-example-location.bom)), [Azure](tutorial/locations/azure-example-location.bom), [GCE](tutorial/locations/gce-example-location.bom) and [Blue Box](tutorial/locations/bb-example-location.bom). You can find more information about what is going on in those files [here](tutorial/swarmCluster.html#setup-a-cloud-location).

Now you are all set. The last thing to do is to deploy your Docker Swarm cluster. You can use this [yaml](examples/swarm.yaml){:target="blank"} to getting started:
{% highlight YAML %}
{% include_relative examples/swarm.yaml %}
{% endhighlight %}
