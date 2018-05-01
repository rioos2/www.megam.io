---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Getting Started
description: In this section you'll find basic information about Rio/OS and its features. If you're first time user then you should read the Getting Started section first.


# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    next:
        content: Installing Rio/OS
        url: 'installing'
---

## Introduction

In this section you'll find basic information about [Rio/OS](http://rio.digital) and how to install and use it properly. If you're first time user then you must read the Getting Started section first.


### Rio/OS

Rio OS is the world's first private cloud operating system. Version 2.0 of the OS is code- named `Aventura`.  

For more  information, visit [Rio.digital](http://rio.digital). 

Rio OS focuses on security from the ground up. Rio OS has ability to launch virtual private servers (VPS), containers and blockchain-backed apps. With Rio OS you don't need to think about servers at all.


![Rio/OS Layered Architecture](/doks-theme/assets/images/RIO_OS_LayeredArchitecture.png)


 *Rio OS* is `commercially licensed`. 

 | License Type | Activation | Elapses |
 | Trial Version |  Automatically starts when Rio OS is run | 14 days |
 | Standard Version | Contact [Rio.digital](http://rio.digital) |  perpetual |




## Concepts 

The following concepts are used in Rio OS.

A high-level overview image depicting Rio OS managing  datacenters is listed below.

![Rio/OS (With nodes connected)](/doks-theme/assets/images/RIO_OS_Highlevel.png)


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
- [Ceph](https://ceph.com)
- [OpenIO](https://openio.com)

#### Network

Different subnets consumed by virtual private servers (VPS), containers and blockchain apps. Virtual network on the control plane in nodes Rio OS are configured by administrators from the `Infrastructure` option in `Command Center`.

### Scaling

Scale changes by a developer automatically gets refreshed to add more containers or increase each containers’ resources.

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

DNS managed using powerdns.

### Digital Cloud

Allows users to spin operating systems of your choice (linux - any flavors, freebsd, windows, coreos) and guard them with tight security with access controlled via a mobile app. The digital cloud is wrapped around with blockchain audits.

### Containers

Allows users to use container orchestration using docker from public or private docker registry. This includes automatic workload recovery, security, networking, service discovery, storage and more.

### Blockchain

Provides Developers with tools to deploy their own applications stored in private Git, svn, (*public Github*) with any of these platforms Java, Ruby, Nodejs, Scala, Python, PHP, Golang, Rust-lang, C/C++ whilst utilizing blockchain technologies.

### Powerful CLI

Allows users to effortlessly manage their apps, services, and infrastructure with a powerful Command Line Interface(CLI) and a easy to use Graphical User Interface(GUI).


### Security

#### Identity & Access Management

Fine-grained access control & integration with built-in roles and permisssion. Provide additional spacing using Teams and Organization with more granularity in isolation.

Support for multiple identity providers SAML 2.0 and OpenID Connect.

Import from (LDAP, Active Directory) in Rio OS identity.

#### Secrets

Allows for the secure distribution of sensitive information to running application while maintaining access control and encryption during communication and at rest.


### Public Rio.Marketplace

Rio marketplace is available publicly in [Rio.marketplace](https://marketplace.rioos.xyz) with apps to use. The categories and the curated apps available are shown below. 

#### Blockchain

* [Hyperledger](https://www.hyperledger.org/)
* [Erc20](http://www.ethdocs.org/en/latest/)

#### Developers

* [PHP](https://secure.php.net/)
* [Java](https://www.java.com/en/)
* [Ruby](https://www.ruby-lang.org/en/)
* [Scala](http://scala-lang.org/)
* [Node.js](https://nodejs.org/en/)
* [Python](https://www.python.org/)
* [RustLang](https://www.rust-lang.org/en-US/)
* [OCaml](https://ocaml.org/)

#### Parallel computing

* [NVIDIA CUDA](https://developer.nvidia.com/cuda-zone)

#### Webservers

* [Apache2](https://httpd.apache.org/)
* [Nginx](https://www.nginx.com/resources/wiki/start/index.html)
* [Caddy](https://caddyserver.com/)
										
#### Databases

* [CouchDB](https://couchdb.apache.org/)
* [PostgreSQL](https://www.postgresql.org/)
* [CockroachDB](https://www.cockroachlabs.com/)
* [Memcache](https://www.memcached.org/)
* [MariaDB](https://mariadb.org/)
* [Cassandra](https://cassandra.apache.org/)
* [InfluxDB](https://www.influxdata.com/time-series-platform/influxdb/)
* [Aerospike](https://www.aerospike.com/)
* [RethinkDB](https://www.rethinkdb.com/)
* [Neo4J](https://neo4j.com/)
* [OrientDB](https://orientdb.com/)
* [VoltDB](https://www.voltdb.com/)
* [RavenDB](https://ravendb.net/)
* [OpenLDAP](http://www.openldap.org/)