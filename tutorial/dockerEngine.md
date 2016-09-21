---
layout: website-normal
title: Docker Engine Tutorial
---

### Introduction
This tutorial is focussed on deploying a simple, no frills, docker engine. 

This is useful if you want to explore docker and its functionality without needing to install and manage docker itself.

### Instructions

1. From your AMP Install, head to the AMP Welcome page. 
1. In the quick deploy section select "Docker Engine" and the location that you want to deploy to. 

AMP will then provision a VM in that location, install Docker and run a Docker Daemon.

To use your new Docker install we must SSH into the VM. The sensor "host.sshAddress" will provide the endpoint and username required to SSH to the VM. 

The SSH key setup in Brooklyn configuration should be used. Once SSH'ed into the machine you can run "Docker" commands as usual.


