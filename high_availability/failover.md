---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Failover of Nodes
description: What happens when the nodes fail. How does Rio/OS manage the failover of running digital cloud, containers, blockchain backed apps in those nodes.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Failover of Rio OS software
        url: '/high_availability'
    next:
        content: Command Center
        url: '/command_center'
---

## High Availability of Nodes

Rio/OS software manages the entity - `Digital Cloud`, `Containers` and `blockchain backed apps` which runs in the cluster of nodes. 

The nodes can fail resulting in the downtime for the business.  **This impacts the ROI for the business.** 

The following sections discusses the **layers of failures** and how they are handled in Rio/OS for `Digital Cloud`, `Containers` and `Blockchain backed apps`.

### Layer 1: Network 

The nodes themselves are healthy. But the network fails in some of the nodes. 

In this scenario, Rio/OS handles the failure as below.

*Time to recover:* `Instant (few seconds)`

#### Digital Cloud

To make sure the digital cloud runs rock solid with the software installed inside the digital cloud the typical loadbalanced architecture must be setup `manually`.

#### Containers  & Blockchain backed apps

To make sure the [Rio/OS containers](/docs/getting_started/) run rock solid the typical loadbalanced architecture as shown below is provided using the [Rio/OS Horizontal scaler](/docs/scaling) 

![Rio/OS software behind loadbalancer](/docs/doks-theme/assets/images/system_requirements/ha_failover.png)

### Layer 2: Nodes fail inside a locatioin

Some of the Nodes failure in a location.

The state of nodes of Rio OS is periodically replicated in the storage in the same location. 

*Time to recover:* `Instant (few seconds)`

There are 2 kinds strategy to choose for Rio OS customers. 

#### Recreate

In this strategy, a `new copy` of the affected entity is spinned off in another node inside the same location. 

<div class="callout callout--warning">
    <p><strong>State recovered</strong>This strategy starts from the initial clean state of the entity. The delta state of the entity (or) as-is state of the entity is lost.</p> 
</div>

*Example*

`Node1` in Location **New York** is `down`. 

All the affected entity in `Node1` is recreated into `Node2` in Location **New York**.

#### RollingUpdate

In this strategy is on, then the clone of affected entity is spinned off in another node inside the same location. 

<div class="callout callout--info">
    <p><strong>State recovered</strong>This strategy starts from the current state of the entity. All the delta state of the entity (or) as-is state of the entity when the failure occurrs is transferred.</p> 
</div>

*Example*

`Node1` in Location **New York** is `down`. 

All the affected entity in `Node1` is cloned into `Node2` in Location **New York**. 


#### Digital Cloud

To make sure the digital cloud runs rock solid with the software installed inside the digital cloud it must be deployed using one of the strategies mentioned above.

<div class="callout callout--info">
    <p><strong>Strategies supported</strong>Both <b>Recreate</b> and <b>RollingUpdate</b> strategies are supported for DigitalCloud.</p>
    <p>After the move to the new node, the old digitalcloud entity in the failed node is removed when the failed node is healthy again.</p>
</div>


#### Containers & Blockchain backed apps

To make sure the containers runs rock solid with the software installed inside the digital cloud it must be deployed using one of the strategies mentioned above.

<div class="callout callout--warning">
    <p><strong>Strategies supported</strong>Only <b>Recreate</b> strategy is supported for Containers at the moment.</p> <p><b>RollingUpdate</b> strategy will be supported for Containers shortly.</p> <p>After the move to the new node, the old container in the failed node is removed when the failed node is healthy again.</p> 
</div>

### Layer 3: Location failure

All of the nodes in a location fails.

*Example*

`All Nodes` in Location **New York** are `down`. 

The state of nodes of Rio OS is periodically replicated in the same storage across locations.

*Time to recover:* `Mostly Instant (few seconds) depending on bandwith`

There are 3 kinds strategy to choose for Rio OS customers. 

#### Recreate

In this strategy a `new copy` of the affected entity is spinned off in another location. 

<div class="callout callout--info">
    <p><strong>State Recovered</strong>This strategy starts from the initial clean state of the entity. The delta state of the entity (or) as-is state of the entity is lost.</p> 
</div>

*Example*

`Node1` in Location **New York** is `down`. 

All the affected entity in `Node1` is recreated into `Node1` in Location **Tokyo**.

#### RollingUpdate

In this strategy a `clone` of affected entity is spinned off in another location. 

<div class="callout callout--info">
    <p><strong>State Recovered</strong>This strategy starts from the current state of the entity. All the delta state of the entity (or) as-is state of the entity when the failure occurrs is transferred.</p> 
</div>

*Example*

`Node1` in Location **New York** is `down`. 

All the affected entity in `Node1` is cloned into `Node1` in Location **Tokyo**.

#### Manual

Periodic backups can be pushed to an offsite backup storage. When a failure occurs, all the copies from the offsite backup are moved to the new location and recreated. 

<div class="callout callout--info">
    <p><strong>State Recovered</strong>This strategy results in data loss. The delta state since the last backup is lost.</p> 
</div>

*Time to recover:* `Very high (few hours) depending on bandwith`

#### Digital Cloud

To make sure the digital cloud runs rock solid with the software installed inside the digital cloud it must be deployed using one of the strategies mentioned above.

<div class="callout callout--info">
    <p><strong>Strategies supported</strong>Both <b>Recreate</b> and <b>RollingUpdate</b> strategies are supported for DigitalCloud.</p>
    <p>After the move to the new node, the old digitalcloud entity in the failed node is removed when the failed node is healthy again.</p>
</div>


#### Containers & Blockchain backed apps

To make sure the containers runs rock solid with the software installed inside the digital cloud it must be deployed using one of the strategies mentioned above.

<div class="callout callout--warning">
    <p><strong>Strategies supported</strong>Only <b>Recreate</b> strategy is supported for Containers at the moment.</p> <p><b>RollingUpdate</b> strategy will be supported for Containers shortly.</p> <p>After the move to the new node, the old container in the failed node is removed when the failed node is healthy again.</p> 
</div>


