---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Virtual Networks
description: Rio OS virtual networks allow applying networks to any node. Read to setup a virtual network.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Nodes
        url: '../../nodes/index.html'
    next:
        content: Storages
        url: '../../storages/index.html'
---

## Virtual Networks


Virtual Network enables a data center to provision the most suitable and efficient networking structure for the applications it hosts. And to alter that structure as conditions warrant, using software rather than requiring physical changes in connections to hardware.


![Rio/OS Virtual Network](/doks-theme/assets/images/Rio_OS_Virtual_Network.png)

Nodes have the actual bridges setup with physical network attached. Rio OS connects to virtual networks via API for setting up networking to cloud workloads. 

### Installation

Every node needs this software to be installed.

#### Clean Install

Boot the node with [USB (Rio OS ISO)](/install#iso) and follow the options prompted.

####  Existing Rio OS node

```


sudo apt-add-repository "deb [arch=amd64] https://registry.rioos.xyz/repo/rioos/aventura/2.0.0-rc1/testing  aventura testing"

sudo apt-get -y update

sudo apt-get install rioos-network


```


> Setup virtual network in Rio OS

To create a virtual network, Refer [Asciicast in cli](/cli). You must have the `netmask`, `subnet cidr range`, `subnet gateway`. The first ip and the last ip in the range are ignored. 

```
netmask =
subnet gateway = 
cidr = 

The available ips are [ , , , ]

The ip [.0]   is used as 
The ip [.254] is used as broadcast
```


The virtual networks are applied to the nodes when a location is created.

<div class="callout callout--info">
    <p><strong>Location - What is it ?</strong> A group of nodes, virtual network and storage identified by a name.</p>    
</div>

Rio OS automatically manages used and unsed ips from the range provided for a node.


