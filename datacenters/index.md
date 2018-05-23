---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Datacenters
description: This section provides ability to create a location which is a grouping inside a datacenter.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: CLI
        url: '/cli/index.html'
    next:
        content: Nodes
        url: '/nodes/index.html'
---


## Datacenters

A Datacenter is a cluster of group of nodes, networking and storage identified by a name called location. 

You can group as many clusters as you can and identify them with location names.

![A cluster of nodes with private and public networking/local storage grouped in Location NEWYORK 01](/docs/doks-theme/assets/images/infra/RIO_OS_Datacenter.png)



### Location

> Deployment is based on location


A location has multiple nodes. Network is attached to each node. *Make sure the storage and network are setup before a location is created*.

#### Create a location

**CLI**

Watch [asciinema](/docs/cli) to create a location.

**UI**

Click > **Locations** > **Create**

![A cluster of nodes with private and public networking/local storage grouped in Location NEWYORK 01](/docs/doks-theme/assets/images/infra/create_location.png)


Click > **Create**


![A cluster of nodes with private and public networking/local storage grouped in Location NEWYORK 01](/docs/doks-theme/assets/images/infra/create_location.png)


The newly created location is listed as below.

![A cluster of nodes with private and public networking/local storage grouped in Location NEWYORK 01](/docs/doks-theme/assets/images/infra/create_location_done.png)