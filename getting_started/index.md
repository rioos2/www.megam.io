---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Getting Started
description: In this section you'll find basic information about Rio OS and its features. If you are a first time user then you must read the Getting Started section first.


# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    next:
        content: Plan Rio/OS (System Requirements)
        url: '/getting_started/system_requirements'
---

## Introduction

In this section you'll find information about [Rio/OS](http://rio.digital){:target="_blank"} and how to install and use it properly. If you're first time user then you must read the Getting Started section first.


### Rio/OS

Rio OS is the world's first private cloud operating system. Version 2.0 of the OS is code- named `Aventura`.  

For more  information, visit [Rio.digital](http://rio.digital){:target="_blank"}. 

Rio OS focuses on security from the ground up. Rio OS has ability to launch virtual private servers (VPS), containers and blockchain-backed apps. With Rio OS you don't need to think about servers at all.


![Rio/OS Layered Architecture](/docs/doks-theme/assets/images/RIO_OS_LayeredArchitecture.png)


 *Rio OS* is `commercially licensed`. 

 | License Type | Activation | Elapses |
 | Trial Version |  Automatically starts when Rio OS is run | 14 days |
 | Standard Version | Contact [sales@rio.company](mailto::sales@rio.company){:target="_blank"} |  perpetual |




## Concepts 

The following concepts are used in Rio OS.

A high-level overview image depicting Rio OS managing  datacenters is listed below.

![Rio/OS (With nodes connected)](/docs/doks-theme/assets/images/RIO_OS_Highlevel.png)


### Datacenter

A Datacenter is a grouped cluster of nodes. A node is a bare metal machine.

#### Locations

A location is a virtual grouping of clustered nodes with storage and networking.  

Rio OS admins have the ability to group nodes as clusters, manage nodes, setup storage and group them to named identifiers. (ex: NEWYORK01, MIAMI01, PARIS02). 

#### Clusters
 
A cluster is a group of nodes. Rio OS scheduler distributes jobs intelligently across a cluster of nodes and datacenters.


#### Nodes

A node is a physical machine. Rio OS onboards nodes automatically.

 
#### Storages

Storage is a collection of disks in nodes consumed by virtual private servers, containers and blockchain apps. Rio OS supports plugins to utilize the below storage types.

- Local
- Network File System (NFS)
- [Ceph](https://ceph.com){:target="_blank"}
- [OpenIO](https://openio.io){:target="_blank"}

#### Network

Different subnets are consumed by virtual private servers (VPS), containers and blockchain-backed apps. To enable management of networking in VPS, containers and blockchain backed apps, an API driven Virtual network on the control plane in Rio OS orchestrates nodes. Easy configuration of Virtual Network by administrators from the `Command Center`.

### Scaling

Scale add more containers or increase each container's resources.

#### Horizontal

Scale apps behind a load balancer to add more containers.

#### Vertical

Scale apps behind cloud orchestration software in order to add more resources to each container.

### High Availability

Self-Healing Infrastructure automatically detects node and workload failures, and automatically recovers workloads. In this situation, without the need to configure anything.


#### Zero Downtime Deployment

Allows users to deploy and update applications anytime with self-service deployment strategies like blue green and canary deployment.

#### Non-Disruptive Upgrades 

Allows users to upgrade RIO/OS without any Disruptions to their service or need to migrate running containers and/or data workloads.

### CI/CD

Code changes by a developer automatically gets refreshed.

#### Private DNS

Setup your own DNS, manage business applications like you do in public using names. DNS is managed using scalable PowerDNS.

### Digital Cloud

Allows users to spin operating systems of your choice (Linux - any flavors, FreeBSD, Windows, CoreOS) and guard them with tight security with access controlled via a mobile app.

### Containers

Allows users to use container orchestration using docker from public or private docker registry. This includes automatic workload recovery, security, networking, service discovery, storage and more.

### Blockchain

Provides Developers with tools to deploy their own applications stored in private Git, (*public Github*) with any of these platforms Java, Ruby, Nodejs, Scala, Python, PHP, Golang, Rust-lang, C/C++ whilst utilizing blockchain technologies.

### Powerful CLI

Allows users to effortlessly manage their apps, services, and infrastructure with a powerful Command Line Interface(CLI).


### Security

#### Identity & Access Management

Fine-grained access control & integration with built-in roles and permisssion. Provide additional spacing using Origin and Teams with more granularity in isolation.

Support for multiple identity providers SAML 2.0 and OpenID Connect.

Import from (LDAP, Active Directory) seamlessly into Rio OS Identity.

#### Secrets

Allows for the secure distribution of sensitive information to running application while maintaining access control and encryption during communication and at rest.


### Public Rio.Marketplace

Headless Rio marketplace is available public at [Rio.marketplace](https://marketplace.rioos.xyz){:target="_blank"} with useful apps to use. The categories and their curated apps are shown below. 

#### Blockchain

* [Hyperledger](https://www.hyperledger.org/){:target="_blank"}
* [Erc20](http://www.ethdocs.org/en/latest/){:target="_blank"}

#### Developers

* [PHP](https://secure.php.net/){:target="_blank"}
* [Java](https://www.java.com/en/){:target="_blank"}
* [Ruby](https://www.ruby-lang.org/en/){:target="_blank"}
* [Scala](http://scala-lang.org/){:target="_blank"}
* [Node.js](https://nodejs.org/en/){:target="_blank"}
* [Python](https://www.python.org/){:target="_blank"}
* [RustLang](https://www.rust-lang.org/en-US/){:target="_blank"}
* [OCaml](https://ocaml.org/){:target="_blank"}

#### Parallel computing

* [NVIDIA CUDA](https://developer.nvidia.com/cuda-zone){:target="_blank"}

#### Webservers

* [Apache2](https://httpd.apache.org/){:target="_blank"}
* [Nginx](https://www.nginx.com/resources/wiki/start/index.html){:target="_blank"}
* [Caddy](https://caddyserver.com/){:target="_blank"}
										
#### Databases

* [CouchDB](https://couchdb.apache.org/){:target="_blank"}
* [PostgreSQL](https://www.postgresql.org/){:target="_blank"}
* [CockroachDB](https://www.cockroachlabs.com/){:target="_blank"}
* [Memcache](https://www.memcached.org/){:target="_blank"}
* [MariaDB](https://mariadb.org/){:target="_blank"}
* [Cassandra](https://cassandra.apache.org/){:target="_blank"}
* [InfluxDB](https://www.influxdata.com/time-series-platform/influxdb/){:target="_blank"}
* [Aerospike](https://www.aerospike.com/){:target="_blank"}
* [RethinkDB](https://www.rethinkdb.com/){:target="_blank"}
* [Neo4J](https://neo4j.com/){:target="_blank"}
* [OrientDB](https://orientdb.com/){:target="_blank"}
* [VoltDB](https://www.voltdb.com/){:target="_blank"}
* [RavenDB](https://ravendb.net/){:target="_blank"}
* [OpenLDAP](http://www.openldap.org/){:target="_blank"}