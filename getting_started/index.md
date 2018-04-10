---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Getting Started
description: In this section you'll find basic information about Rio/OS and how to install it and use it properly. If you're first time user then you should read Getting Started section first.


# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    next:
        content: Installing Rio/OS
        url: 'installing'
---

## Introduction

In this section you'll find basic information about [Rio/OS](http://rio.digital) and how to install it and use it properly. If you're first time user then you must read Getting Started section first.


### Rio/OS

Rio OS is the worlds first private cloud operating system. This version 2.0 of the os is code named `Aventura`.  

Rio OS is  commercially licensed. For more  information, visit [rio.digital](http://rio.digital). With Rio OS you don't need to think about servers at all. 

![Rio/OS Architecture](http://via.placeholder.com/550x350)
 
Ri OS focuses on security from the ground up which has ability to launch digital cloud, containers and blockchain apps.

![Rio/OS Layered Architecture](http://via.placeholder.com/550x350)


<>

The features of Rio OS are described below.

### Datacenter

A Datacenter is a grouped cluster of nodes. A node is a bare metal machine.

#### Locations

A location is a virtual grouping of cluster with storage and network to use.  Rio OS admins have ability to group nodes as clusters, manage nodes, setup storage and group them to named identifiers (eg: NEWYORK_01, MIAMI_02). 


#### Clusters
 
A cluster is a group of nodes. Rio OS scheduler distributes jobs intelligently across a cluster of nodes and datacenters.


#### Nodes

A node is a physical machine. Rio OS onboards nodes automatically.

 
#### Storages

Storage are created automatically using the supported plugins for 

- Local
- Network File System (NFS)
- [Ceph](https://ceph.com)

#### Network

Virtual network is managed by Rio OS upon install automatically.

### Scaling

Code changes by a developer automatically gets refreshed.

#### Horizontal

Scale apps behind a load balancer

#### Vertical


### High Availability

Self-Healing Infrastructure automatically detects node and workload failures, automatically recovers workloads in this situation without the need to configure anything.


#### Zero Downtime Deployment

Allows users to deploy and update applications anytime with self-service deployment strategies like blue green and canary deployment.

#### Non-Disruptive Upgrades 

Allows users to upgrade RIO/OS without any Disruptions to their service or migrating running containers and/or data workloads.

### CI/CD

Code changes by a developer automatically gets refreshed.

Scale apps behind a load balancer

#### Private DNS

DNS managed using powerdns or atomia dns or coredns

### Digital Cloud

Allows users to spin operating systems of your choice (linux - any flavors, freebsd, windows, coreos) and guard them with tight security with access controlled via a mobile app.

### Containers

Allows users to use container orchestration using docker from public or private docker registry. This includes automatic workload recovery, security, networking, service discovery, storage and more.

### Blockchain

Developers to deploy their own applications stored in private Git, svn, (*public Github*) with any of these platforms Java, Ruby, Nodejs, Scala, Python, PHP, Golang, Rust-lang, C/C++.

### Powerful CLI

Allows users to effortlessly manage their apps, services, and infrastructure with a powerful Command Line Interface(CLI) and a easy to use Graphical User Interface(GUI).


### Security

#### Identity & Access Management

Fine-grained access control & integration with multiple identity providers (LDAP, Active Directory, SAML 2.0 and OpenID Connect).

#### Secrets Management

Allows for the secure distribution of sensitive information to running application while maintaining access control and encryption during communication and at rest.



### Rio.Marketplace


#### Blockchain

Hyperledger, Erc20

#### Developers

PHP, Java, Ruby, Scala, Node.js, Python, RustLang, OCaml

#### Parallel computing

CUDA

#### Webservers

nginx
										
#### Databases

CouchDB, PostgreSQL, CockroachDB, Memcache, MariaDB, Cassandra, InfluxDB, Aerospike, RethinkDB, Neo4J, OrientDB, VoltDB, RavenDB,  OpenLDAP