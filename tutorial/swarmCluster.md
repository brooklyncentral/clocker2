---
layout: base
title: Swarm Cluster Tutorial
---

### Introduction
This tutorial is focussed on deploying a production ready swarm cluster.

### Overview
The production ready swarm cluster is comprised of the following components:

### Pre-requisites

This tutorial assumes you have [installed](./tutorial-get-amp-running.html) Cloudsoft AMP, and the AMP CLI.

#### A load-balanced cluster of swarm managers
Swarm managers control a swarm's nodes and dictate the node on which containers are deployed.
We interact directly with the swarm manager cluster's load balancer as if it were a single docker node.
The load-balancer will redirect traffic to a healthy manager when a manager fails.  The replacer policy will detect the failure and replace the failed manager.

#### A cluster of swarm nodes
These nodes are where docker containers are deployed to. The cluster has an AutoScalerPolicy and will scale up due to high CPU usage.

#### etcd Cluster
Used as a discovery backend for the swarm cluster.

#### CA Server
This is used to provide TLS certificates for the swarm cluster. This component is designed to be easily replaced. It is strongly recommended that this component is replaced with a production grade CA server of your choice.


### Instructions

#### Setup a cloud location
Firstly, we need to setup a location to deploy the Swarm cluster to.  We recommend the following settings:

- use the `installDevUrandom` config to prevent installation speed being slowed by lack of entropy. See [Entropy Troubleshooting](/operations/troubleshooting/increase-entropy.html)
- use at least 2GB RAM
- use a CentOS 7 based image

The following catalog items should enable you to quickly get started on some popular clouds.  Download the .bom file of the relevant cloud, add your credentials, and then run:

    br add-catalog <CLOUD-PROVIDER>-example-location.bom

{::options parse_block_html="true" /}

<ul class="nav nav-tabs">
    <li class="active impl-1-tab"><a data-target="#impl-1, .impl-1-tab" data-toggle="tab" href="#">AWS</a></li>
    <li class="impl-2-tab"><a data-target="#impl-2, .impl-2-tab" data-toggle="tab" href="#">SoftLayer</a></li>
    <li class="impl-3-tab"><a data-target="#impl-3, .impl-3-tab" data-toggle="tab" href="#">Azure</a></li>
    <li class="impl-4-tab"><a data-target="#impl-4, .impl-4-tab" data-toggle="tab" href="#">GCE</a></li>
    <li class="impl-5-tab"><a data-target="#impl-5, .impl-5-tab" data-toggle="tab" href="#">Blue Box</a></li>
</ul>

<div class="tab-content">
<div id="impl-1" class="tab-pane fade in active">
{% highlight yaml %}
{% include_relative locations/aws-example-location.bom %}
{% endhighlight %}
[aws-example-location.bom](locations/aws-example-location.bom){:target="blank"}
</div>
<div id="impl-2" class="tab-pane fade">
{% highlight yaml %}
{% include_relative locations/sl-example-location.bom %}
{% endhighlight %}
[sl-example-location.bom](locations/sl-example-location.bom){:target="blank"}
</div>
<div id="impl-3" class="tab-pane fade">
{% highlight yaml %}
{% include_relative locations/azure-example-location.bom %}
{% endhighlight %}
[azure-example-location.bom](locations/azure-example-location.bom){:target="blank"}
</div>
<div id="impl-4" class="tab-pane fade">
{% highlight yaml %}
{% include_relative locations/gce-example-location.bom %}
{% endhighlight %}
[gce-example-location.bom](locations/gce-example-location.bom){:target="blank"}
</div>
<div id="impl-5" class="tab-pane fade">
{% highlight yaml %}
{% include_relative locations/bb-example-location.bom %}
{% endhighlight %}
[bb-example-location.bom](locations/bb-example-location.bom){:target="blank"}
</div>
</div>

#### Deploy a Swarm Cluster
After the location is setup, it is time to deploy a Swarm cluster. From your AMP Install, head to the AMP Welcome page. In the quick deploy section select "Docker Swarm with Discovery and CA" and select the location that that we setup in the previous step. You can also change some configuration options such as the minimum and maximum number of nodes. Once you are happy with the configuration press Deploy and your swarm cluster will be created.

To interact with the swarm cluster, we first need to get certificates from the CA server. To do so, the following [script](getcert.sh){:target="blank"} can be used:
{% highlight bash %}
{% include_relative getcert.sh %}
{% endhighlight %}

To communicate with the cluster, you must communicate directly with the swarm master. To do so, first retrieve the Swarm master URI and port. This can be found by checking for the "host.name" and "swarm.port" sensor. After, ensure you have the docker CLI installed then set up the following environemnt variables:
{% highlight bash %}
export DOCKER_HOST=tcp://<Swarm Master URI & port>
export DOCKER_TLS_VERIFY=true
export DOCKER_CERT_PATH=<CERT_DIR>
{% endhighlight %}

You will now be able to run docker commands against the swarm cluster.
