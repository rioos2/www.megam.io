---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: High Availability - Rio/OS 
description: Handy steps for deploying RioOS in HA

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Plan Rio OS install
        url: '/getting_started/system_requirements'
    next:
        content: Failover of Nodes 
        url: '/high_availability/failover'
---

# HA: Rio/OS Software 

Rio/OS software itself can fail. To handle failure.

### Layer 1: Network 

To make sure the [Rio/OS components](/docs/getting_started/) run rock solid the typical active-active, load balanced architecture as shown below is used. 

![Rio/OS software behind loadbalancer](/docs/doks-theme/assets/images/system_requirements/ha_failover.png)

#### Active/Active

Traffic intended for the failed node is either passed onto an existing node or load balanced across the remaining nodes. This is usually only possible when the nodes use a homogeneous software configuration.

#### Pacemaker

Pacemaker was born out of the Linux-HA project as an advanced resource manager that could use heartbeat for cluster membership and communication.

#### Heartbeat

Heartbeat is a daemon that provides cluster infrastructure (communication and membership) services to its clients. This allows clients to know about the presence (or disappearance!) of peer processes on other machines and to easily exchange messages with them. In order to be useful to users, the Heartbeat daemon needs to be combined with a cluster resource manager (CRM) which has the task of starting and stopping the services (IP addresses, web servers, etc.) that cluster will make highly available. We will use pacemaker as this is the preferred cluster resource manager for clusters based on Heartbeat.


### Layer 2: Nodes

If one of the node is down then Rio OS will keep working using the `Layer 1: Network` failover through load balancers.

### Layer 3: 

If both nodes are down in the Rio OS then the state of Rio OS must be recovered from periodic backups in the objectstorage.

## Get Ready to Deploy

Production environments which require high availability involves several architectural requirements. Specifically you will need at least  2 or 3 nodes, and certain components will be deployed in multiple nodes to prevent single points of failure.

We’ll take a closer look at the various option of the deployment in [Plan Rio/OS](/docs/getting_started/system_requirements) 

