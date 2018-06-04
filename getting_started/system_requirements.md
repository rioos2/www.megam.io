---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Plan Rio OS installation. 
description: What are the system requirements for different topologies. 

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Install Rio OS
        url: '/getting_started/installing'
    next:
        content: High Availability
        url: '/high_availability'
---

## Plan : System Requirements


In order to get the most out of  Rio OS, we recommend you to create a plan with the following features:

  * Performance
  * Scalability
  * High availability

This guide provides comprehensive information in such a way that you can easily architect your deployment and utilize the technologies involved in the management of virtualized resources and their relationship.

### Deployment Architecture

We assume that your physical infrastructure adopts a classical cluster-like architecture with a front-end, and a set of hosts where Virtual Machines (VM)/Containers (Docker) or unikernel will be executed.


![Datacenter architecture view](/docs/doks-theme/assets/images/system_requirements/rioos_architecture_overview.png)

We assume that your physical hardware supports Virtualization & adopts a classical cluster-like architecture with a front-end, which is the only specific system requirement.

### Operating System

The supported operating systems are `Ubuntu 16.04/18.04, Debian 8/9 and CentOS 7.x.`

### Hardware Requirements

The basic requirements of hardware for  Rio OS in `minimal`, `high available`  mode are:


### Minimal: Try out.

This mode is a try out configuration. The local storage plugin is used. Refer [here](/storage/) for more information on storage.

This isn't recommended for production use.

![Rio OS Minimum System requirements](/docs/doks-theme/assets/images/system_requirements/rioos_topology_minimal.png)

| Application                     | Description                                                                                     | Quantity                     |
| ------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------- |
| Master                          | Hosts our Rio OS software Stack, such as our provisioning engine and front-end etc.                    | 1                            |
| Compute  | A compute node to host virtual machines with local storage                                                         | > 1                          |



#### Hardware

The hardware requirements in minimal mode are,

|                 | CPU (Cores)	| RAM (GB)	| HDD (TB) | SSD    |
|:----------------|:------------|:----------|:---------|:-------|
| Master          | 8/12   >    |16  >      | 1 x 1TB >|1 x 240GB > |
| Compute/Storage | 6 >         |128        | 1 x 1TB >|1 x 240GB > |


#### Storage Plugin: Local

Local file sytem volumes (directories) present the approach to build storage using commodity hardware attached to compute nodes.

![Topology recommended](/docs/doks-theme/assets/images/system_requirements/rioos_topology_local.png)

Every compute node has its own local volume.


### Highly Avaliable:

This mode is for production ready - highly available configuration. The storage plugins `nfs/ceph` can be used. 

For more information on 

- [Storage Plugins](/docs/storages).
- [Failover of Rio/OS software](/docs/high_availability).
- [Failover of Nodes in a region](/docs/high_availability/failover#in_region).
- [Failover across regions](/docs/high_availability/failover#across_region).

![Rio OS HA system requirements are](/docs/doks-theme/assets/images/system_requirements/rioos_topology_ceph.png)



| Application                     | Description                                                                                     | Quantity                       |
| ------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------ |
| Master                          | Hosts Rio/OS Software Stack, such as our provisioning engine and front-end etc.                    | 1                              |
| Slave                           | Slaves are additional nodes that hosts a copy of the  Rio/OS software, they can be used to loadbalance the platform or used during failover      | 1                              |
| Compute Node  | A compute node to host virtual machines/containers                                                         | > 2                            |
| Storage Node                    | A storage node to power High Availability & Storage Solutions                                   | > 2                            |


#### Hardware


|               | CPU (Cores)   | RAM (GB)     | HDD                                |
| ------------- | ------------- | ------------ | ---------------------------------- |
| Master        | > 8           | > 16GB       | 1xSSD (240GB)                      |
| Slave         | > 8           | > 16GB       | 1xSSD (240GB)                      |
| Compute Node  | > 8           | > 32GB       | > 2xHDD (2TB) (or) 2xSSD (1TB)     |
| Storage Node  | > 8           | > 16GB       | > 4xHDD (2TB) (or) 4xSSD (1TB)     |

#### Storage Plugin: NFS

NFS and its volumes present the approach to build clusters using commodity hardware attached to compute nodes.

![Topology receommended](/docs/doks-theme/assets/images/system_requirements/rioos_topology_local.png)
Every compute node possesses its own LVM volume.

#### Storage Plugin: Ceph

Ceph paves the way to create Storage area network(SAN) clusters using commodity hardware.

![Topology Ceph for HA](/docs/doks-theme/assets/images/system_requirements/rioos_topology_ceph.png)

In this, any number of disks can be pooled to create a ceph cluster.

#### Storage Plugin: My storage isn't listed here.

Great, contact support@rio.company, If you need plugin for other storages (eg: Nexanta, iSCSI, NetApp..).

We release support for more storage plugins periodically.

