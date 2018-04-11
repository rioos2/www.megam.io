---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Installing
description: This section covers the standard procedure to setup Rio/OS 2.0 Aventura using  ISO and another option install Rio/OS ISO image directly on master,node, Storage.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Getting Started
        url: '/getting_started'
    next:
        content: Command Center
        url: '../../command_center/index.html'
---

## Installing

Rio/OS offering two type of installation 

- USB ISO 
- Existing Rio OS using Docker containers


### ISO Installation

ISO packed with all components that sufficient to make a private cloud environment.

how `[Download](http://bit.ly/gdrive)` you

<div class="example">
	aa
    <a href="http://bit.ly/drive#" target="blank">Download</a>
</div>

```
[Download](http://bit.ly/gdrive)
```


> Pardon my fresnch

<div class="callout callout--info">
    <p><strong>Lorem ipsum dolor sit amet!</strong> Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
</div>



### Components


<table>
  <tr>
   <td>Code name
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>Rio/OS UI
   </td>
   <td>User interface to manage and control Rio/OS
   </td>
  </tr>
  <tr>
   <td>Controller
   </td>
   <td>Rio/OS Controller daemon
   </td>
  </tr>
  <tr>
   <td>Scheduler
   </td>
   <td>Rio/OS Scheduler daemon
   </td>
  </tr>
  <tr>
   <td>Postgres
   </td>
   <td>Rio/OS database storage
   </td>
  </tr>
  <tr>
   <td>Apiserver
   </td>
   <td>API for Rio/OS. The heart of the system which acts as the mediator for Rio/OS
   </td>
  </tr>
  <tr>
   <td>Prometheus
   </td>
   <td>To get all Metrics data
   </td>
  </tr>
  <tr>
   <td>PowerDNS
   </td>
   <td>Assign domain names for Rio/OS system (base Rio, all VMs and containers)
   </td>
  </tr>
  <tr>
   <td>VNC
   </td>
   <td>VNC Daemon
   </td>
  </tr>
  <tr>
   <td>InfluxDB
   </td>
   <td>Logs storage.
   </td>
  </tr>
  <tr>
   <td>Nodelet
   </td>
   <td>Rio/OS compute package. Run all node systems 
   </td>
  </tr>
  <tr>
   <td>Fluent-bit
   </td>
   <td>Logs collector
   </td>
  </tr>
  <tr>
   <td>Storlet
   </td>
   <td>Rio/OS storage manager
   </td>
  </tr>
</table>



## Master

Let's assume we have Master, Server and Storage systems. And assume boot Rio/OS manually via some plug and play device. When booting Rio/OS it will ask select which system want to install it. Simply select "Master System". Then all the installation process will be happen automatically.

**The component will run on Master system.**



*   Rio/OS UI
*   VNC server
*   Controller
*   Api server
*   Scheduler
*   Prometheus
*   PowerDNS
*   Postgres
*   InfluxDB


## Node

Each and every servers consider as a node in Rio/OS. Even we can also using master as one of server (node).  

When the time of ISO boot it will asking Which system want to install. Select "Node System". Then it will install all necessary components and packages.

**The component will run on Server system.**



*   Nodelet
*   Fluent-bit


## Storage

VM and Container consuming space from storage server and the compute resource of VM/Container will be from nodes. 

When the time of ISO boot it will asking Which system want to install. Select "Storage System". Then it will ask which type of storage system want to install (NFS, CEPH,..). After selecting storage system type then it will proceed further automatically.

**The component will run on Server system.**



*   Storlet


### Voila !

You have successfully installed Rio/OS packages.


## Manual

Rio/OS provide docker private registry where all packages are layed. So need to pull image from docker private registry and run it manually.

 Setup Docker


```
$ sudo apt-get install wget curl

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs) stable"

$ sudo apt-get update -y

$ sudo apt-get install -y docker-ce
```


Give sudo permission for docker user, helps not to type sudo docker <command> for all the commands.


```
$ sudo usermod -aG docker ${USER}
```


**Run docker**


```
$ sudo systemctl start docker

$ sudo systemctl status docker
```


### Registry

**Download the ca certificate**

This needed to access the private registry behind TLS.


```
https://drive.google.com/open?id=1s43DatiJHgbdXNdlcc8TYYW0AlA3vLIL
```


**Create /etc/docker/certs.d**

The objective is to copy the downloaded ca.crt into /etc/docker/certs.d/registry.riocorp.io:5000 directory


```
$ sudo -s

$ export CA_CRT=$PWD/ca.crt

$ mkdir -p /etc/docker/certs.d/registry.riocorp.io:5000

$ mv $CA_CRT /etc/docker/certs.d/registry.riocorp.io:5000

$ exit
```


**Pull and run from private registry**


```
$ docker login registry.riocorp.io:5000
```


userid rioosadmin    password team4rio 


### Master

After successfully accessing the Rio/OS private registry. We can good to go to pull and run docker image directly.

Master system is primary system to run most of the Rio/OS component. Components which need to run on master server are mentioned below.


<table>
  <tr>
   <td>Code name
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>Rio/OS UI
   </td>
   <td>Web UI for Rio/OS Platform
   </td>
  </tr>
  <tr>
   <td>VNC Server
   </td>
   <td>Rio/OS VNC daemon
   </td>
  </tr>
  <tr>
   <td>Controller
   </td>
   <td>Rio/OS Controller daemon
   </td>
  </tr>
  <tr>
   <td>Scheduler
   </td>
   <td>Rio/OS Scheduler daemon
   </td>
  </tr>
  <tr>
   <td>Postgres
   </td>
   <td>Rio/OS database storage
   </td>
  </tr>
  <tr>
   <td>Apiserver
   </td>
   <td>Intermediate to all Rio/OS packages
   </td>
  </tr>
  <tr>
   <td>Prometheus
   </td>
   <td>To get all Metrics data
   </td>
  </tr>
  <tr>
   <td>PowerDNS
   </td>
   <td>Assign domain name to Rio package, all VMs and containers
   </td>
  </tr>
  <tr>
   <td>InfluxDB
   </td>
   <td>Logs storage
   </td>
  </tr>
</table>


**Pre-requisites**



*   Access to Rio/OS registry.

**Note**

192.168.2.47 is master system IP address.



*   Rio/OS UI

User interface (UI/UX) of Rio/OS.


```
$ sudo docker run -d -p 192.168.2.47:80:4200 --name=rioosui registry.riocorp.io:5000/rioosui:2.0
```




*   VNC Server

```
$ sudo docker run -d  -p 192.168.2.47::8000:8000 --name=rioosvnc --restart always registry.riocorp.io:5000/rioosvnc:2.0

```

*   Controller & Scheduler

```

$ sudo docker run -d -p 192.168.2.47::10252:10252 --name=riooscontroller -v /var/lib/rioos/controller:/var/lib/rioos/controller --restart always registry.riocorp.io:5000/riooscontroller:2.0

$ sudo docker run -d -p 192.168.2.47::10251:10251 --name=rioosscheduler -v /var/lib/rioos/scheduler:/var/lib/rioos/scheduler --restart always registry.riocorp.io:5000/rioosscheduler:2.0
```


*   Postgres

This is used to store all Rio/OS data and DNS records


```
$ sudo docker run -d --name rioospostgres -e POSTGRES_PASSWORD=supersecret -v /var/lib/rioos/postgres-data:/var/lib/postgresql --restart always registry.riocorp.io:5000/rioospostgres:10.1
```




*   Apiserver

Central body of Rio/OS. This is an Intermediary of UI, controller, scheduler, nodelet and storlet


```
$ sudo docker run -d -p 192.168.2.47:9636:9636 --name=rioosapiserver registry.riocorp.io:5000/rioosapiserver:2.0
```




*   Prometheus

This is used to pull metrics for all virtual machine


```
$ sudo docker run -d  -p 192.168.2.47::9090:9090 --name=prometheus --restart always registry.riocorp.io:5000/prometheus:2.0.0
```




*   PowerDNS

Assign domain name to Rio/OS packages and all running VM, Container


```
$ sudo docker run -d --name rioospowerdns --link rioopostgres:postgres -p 192.168.2.47:53:53 -p 192.168.2.47:53:53/udp -e AUTOCONF=postgres -e PGSQL_USER=postgres -e PGSQL_PASS=supersecret --restart always registry.riocorp.io:5000/rioospowerdns:4.0.2 --cache-ttl=120 --allow-axfr-ips=127.0.0.1
```




*   InfluxDB 

This is an backend of Fluent-bit. All log data are stored in influxDB


```
$ sudo docker run -d --name influx -p 192.168.2.47:8086:8086 -v /var/lib/rioos/influxdb:/var/lib/influxdb registry.riocorp.io:5000/rioosinfluxdb:1.3.7
```


### Node

As now we provide deb packages for nodelet, fluent-bit. Repeat this step to all node. 


```

$ sudo apt-add-repository "deb [arch=amd64] https://get.riocorp.io/repo/2.0/ubuntu/16.04/testing xenial testing"

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611
$ sudo apt-get update
$ sudo apt-get install -y rioos-nodelet rioos-network rioos-fluentbit

```


```

$ sudo apt-get install -y nfs-common

```


Now, You have to successfully Installed nodelet, fluent-bit into your system and its running.

### Storage

As now we provide deb packages for storelet. 


#### Pre-requisites

*   If you are using NFS storage, need to install NFS server


#### NFS 


#### About NFS

**Network File System** (**NFS**) is a distributed file system protocol originally developed by Sun Microsystems in 1984,<sup> </sup>allowing a user on a client computer to access files over a computer network much like local storage is accessed.


#### Install


```
$ sudo apt-get install -y nfs-kernel-server
```


Now, You have installed NFS server.


#### Storlet Install


```
$ sudo apt-add-repository "deb [arch=amd64] https://get.riocorp.io/repo/2.0/ubuntu/16.04/testing xenial testing"

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611

$ sudo apt-get update

$ sudo apt-get install -y rioosstorelet
```


Now, You are installed storlet in your system. It's automatically handshake into storage client system


## Datacenter

This lesson helps to complete UI configuration on Rio/OS. We will cover the following



*   Connect compute
*   Create NFS storage and mount disks
*   Configure Network(subnets)
*   Create Datacenter and configure nodes, networks, storages under datacenter


### Connect Compute


### Create NFS storage & mount Disks


### Configure Network


### Create Datacenter



Voila !

You have successfully completed the tutorial.






