---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Nodes
description: This section provides information on onboarding Nodes and managing them.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Datacenters
        url: '../../datacenters/index.html'
    next:
        content: Networks
        url: '../../networks/index.html'
---

## Nodes

Nodes are the basic element in Rio OS. They provide the basic ingredient - [CPU/GPU, RAM, DISK) for a cloud operating system.

### Nodelet

Nodes are managed by `Nodelet`. Nodelet is an agent that manages the digitalcloud, containers, blockchain apps in the baremetal node.

### Installation

#### Clean Install

Boot the node with [USB (Rio OS ISO)](/install#iso) and follow the options prompted.

####  Existing Rio OS node

```


sudo apt-add-repository "deb [arch=amd64] https://registry.rioos.xyz/repo/rioos/aventura/2.0.0-rc1/testing  aventura testing"

sudo apt-get -y update

sudo apt-get install rioos-nodelet


```

### Configuration

> The configuration `nodelet.rioconfig` exists as created during [installation](/getting_started/installing)

<div class="callout callout--info">
    <p><strong>Changing configuration</strong>There is no need to change the `nodelet.rioconfig` as it is automatically created with strong encryption.</p>    
</div>


### Running


``` 


sudo systemctl stop rioos_nodelet

sudo systemctl start rioos_nodelet


```

To tail the logs of the nodelet

```

sudo journalctl -u rioos_nodelet.service -f

```

### Register

The nodes are registered into Rio OS automatically with the `hostname` and an unique `machine id`.  

To repeat the registration in another node 

- Copy the `/var/lib/rioos/config/nodelet.rioconfig` 
- Perform the installation

You will see the additional nodes displayed in the [command center](/command_center)