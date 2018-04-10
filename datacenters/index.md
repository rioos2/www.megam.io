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
        url: '../../cli/index.html'
    next:
        content: Nodes
        url: '../../nodes/index.html'
---


## Datacenters

A Datacenter is a cluster of group of nodes, networking and storage identified by a name called location. 

You can group as many clusters as you can and identify them with different location names.

![A cluster of nodes with private and public networking/local storage grouped in lLocation NEWYORK 01](http://via.placeholder.com/550x350)


### Location

> Deployment is based on location


A location has multiple nodes. Network is attached to the node. Make sure the storage and network are setup before a location is created.

To create a location, Refer [Asciicast in cli](/cli)

![User deploying in location NEWYORK 01](http://via.placeholder.com/550x350)

Upon configuration the location  appears in the [Rio OS user interface](/command_center).