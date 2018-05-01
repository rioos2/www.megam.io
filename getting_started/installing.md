---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Installing
description: This section covers the standard procedure to setup Rio/OS 2.0 *Aventura* using an ISO and another option too install Rio/OS ISO image directly on the master, node and Storage.

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

## Installation

Rio/OS offering two type of installation 

- USB ISO 
- Existing OS using Docker containers and native packages (deb, rpm)


### What is installed ?

The Rio OS components are grouped as per the pic.

![Rio/OS Components](/doks-theme/assets/images/RIO_OS_Highlevel.png)


<table>
  <tr>
   <td>Code name
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>UI
   </td>
   <td>Command center of  Rio/OS
   </td>
  </tr>
  <tr>
   <td>Controller
   </td>
   <td>Controller to manage state of the Rio OS abstractions
   </td>
  </tr>
  <tr>
   <td>Scheduler
   </td>
   <td>Scheduler that schedules jobs across the datacenter
   </td>
  </tr>
  <tr>
   <td>PostgreSQL
   </td>
   <td>Persistant storage
   </td>
  </tr>
  <tr>
   <td>API Server
   </td>
   <td>API for Rio/OS. The heart of the system which acts as the mediator for Rio/OS system components.
   </td>
  </tr>
  <tr>
   <td>Telemtry
   </td>
   <td>Metrics collector and analytics of Rio OS 
   </td>
  </tr>
  <tr>
   <td>PowerDNS
   </td>
   <td>Assign domain names for Rio/OS system (base Rio, digital cloud, containers and blockchain apps)
   </td>
  </tr>
  <tr>
   <td>Console
   </td>
   <td>A VNC console proxy to access digital cloud
   </td>
  </tr>
  <tr>
   <td>Blockchain
   </td>
   <td>Audit storage based on blockchain.
   </td>
  </tr>
  <tr>
   <td>Nodelet
   </td>
   <td>Rio/OS compute enabler. Runs all node systems 
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
   <td>Rio/OS storage enabler. Runs on nodes that provides storage.
   </td>
  </tr>
</table>


![Rio/OS Hub and Spoke](/doks-theme/assets/images/RIO_OS_Highlevel.png)

## Master

**A Master contains the Rio OS components.**

*   UI
*   API Server
*   Controller
*   Scheduler
*   Telemetry   
*   PowerDNS
*   PostgreSQL   


## Node

Each and every single server is considered as a node in Rio/OS. We can even use a master node as one of the  servers (node) itself.


**A Node contains the compute, storage and  networking components.**

*   Nodelet
*   Fluent-bit


## Storage

Digital cloud, container and blockchain apps consume space from storage server. 

**A Storage contains the component.**

*   Storlet

### ISO Installation

ISO is packed with Ri OS components that is sufficient to make a private cloud environment.

Contact [sales](sales@rio.company) requesting access to the link.

[Download](http://bit.ly/gdrive)` the ISO from the [here](https://drive.google.com).


<div class="callout callout--info">
    <p><strong>Installing!</strong> Insert the USB in the server. Follow the instructions and you are done.</p> 
</div>


## Manual

Rio/OS comes packaged as a combination of native debian/redhat packages and  docker containers stored in a  private registry.

### Setup Docker


```

sudo apt-get install wget curl

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs) stable"

sudo apt-get update -y

sudo apt-get install -y docker-ce

```

Give sudo permission for docker user, helps not to type `sudo docker <command>` for all the commands.


```
sudo usermod -aG docker ${USER}
```


### Run Docker


```
sudo systemctl start docker

sudo systemctl status docker
```


### Access Registry

Contact [sales](sales@rio.company) requesting access to the link.

#### Download the registry CA certificate

The CA certificate is needed to access the private registry behind TLS.


```

wget https://drive.google.com/open?id=1s43DatiJHgbdXNdlcc8TYYW0AlA3vLIL

```


### Create /etc/docker/certs.d**

Copy the downloaded `ca.crt` into `/etc/docker/certs.d/registry.rioos.xyz:5000` directory


```
sudo -s

export CA_CRT=$PWD/ca.crt

mkdir -p /etc/docker/certs.d/registry.rioos.xyz:5000

mv $CA_CRT /etc/docker/certs.d/registry.rioos.xyz:5000

exit

```

#### Login to registry


```

docker login registry.rioos.xyz:5000

userid: rioosadmin    
password: team4rio 

```

### Install Master

After successfully accessing the Rio/OS private registry. 

<div class="callout callout--info">
    <p><strong>IP Address</strong>In the below sections `192.168.2.47` is used as the  ip address to install Master denoted by $MY_IP_ADDRESS. Replace it with the ip address of your server.
    </p>    
</div>

<div class="callout callout--info">
    <p><strong>Version</strong>2.0.0-rc3 is the latest version tag and in the below install notes. This is subjected to change as we progress denoted by $RIOOS_VERSION_TAG.
    Verify the release notes for newer versions.</p>    
</div>

* export variables

```
export MY_IP_ADDRESS=192.168.2.47

export RIOOS_VERSION=2.0.0.rc3

```

*   Command center for Rio/OS.

```

sudo docker run -d -p $MY_IP_ADDRESS:80:4200 --name=rioosui registry.riocorp.io:5000/rioosui:$RIOOS_VERSION

```

*   Controller & Scheduler

```

sudo docker run -d -p $MY_IP_ADDRESS::10252:10252 --name=riooscontroller -v /var/lib/rioos/controller:/var/lib/rioos/controller --restart always registry.riocorp.io:5000/riooscontroller:$RIOOS_VERSION

sudo docker run -d -p $MY_IP_ADDRESS::10251:10251 --name=rioosscheduler -v /var/lib/rioos/scheduler:/var/lib/rioos/scheduler --restart always registry.riocorp.io:5000/rioosscheduler:$RIOOS_VERSION

```


*   PostgreSQL

This is used to store all Rio/OS data and DNS records


```

sudo docker run -d --name rioospostgres -e POSTGRES_PASSWORD=supersecret -v /var/lib/rioos/postgres-data:/var/lib/postgresql --restart always registry.rioos.xyz:5000/rioospostgres:10.3

```


*   API Server

Central body of Rio/OS. This is an Intermediary to the UI, controller, scheduler, nodelet and storlet. 


```

sudo docker run -d -p $MY_IP_ADDRESS:9636:9636 --name=rioosapiserver registry.riocorp.io:5000/rioosapiserver:$RIOOS_VERSION

```

*   Machine Console Server

```

sudo docker run -d  -p $MY_IP_ADDRESS::8000:8000 --name=rioosvnc --restart always registry.rioos.xyz:5000/rioosvnc:$RIOOS_VERSION

```

*   Blockchain Audits Server

```

sudo docker run -d  -p $MY_IP_ADDRESS::8000:8000 --name=rioosvnc --restart always registry.rioos.xyz:5000/rioosblockchain:$RIOOS_VERSION

```


*   Telemetry

This is used to pull metrics for all virtual machine


```
sudo docker run -d  -p $MY_IP_ADDRESS::9090:9090 --name=prometheus --restart always registry.rioos.xyz:5000/prometheus:$RIOOS_VERSION
```


*   PowerDNS

Assign domain name to Rio/OS packages and all running VM, Container


```

sudo docker run -d --name rioospowerdns --link rioopostgres:postgres -p $MY_IP_ADDRESS:53:53 -p 192.168.2.47:53:53/udp -e AUTOCONF=postgres -e PGSQL_USER=postgres -e PGSQL_PASS=supersecret --restart always registry.rioos.xyz:5000/rioospowerdns:4.0.2 --cache-ttl=120 --allow-axfr-ips=127.0.0.1

```


* Logs Collector

This is an backend of Fluent-bit. All log data are stored in influxDB




* Logs storage plugin for  InfluxDB 

This is an backend of Fluent-bit. All log data are stored in influxDB


```

sudo docker run -d --name influx -p $MY_IP_ADDRESS:8086:8086 -v /var/lib/rioos/influxdb:/var/lib/influxdb registry.rioos.xyz:5000/rioosinfluxdb:1.3.7

```


* Logs storage plugin for  Elastic Search

This is an backend of Fluent-bit. Optional log data are stored in Elastic Search


```

sudo docker run -d --name elasticsearch -p $MY_IP_ADDRESS:8086:8086 -v /var/lib/rioos/influxdb:/var/lib/influxdb registry.rioos.xyz:5000/rioosinfluxdb:1.3.7

```


### Node

The following operating systems are supported. 
 
- Debian  8/9
- CentOS 7.x
- Rio OS Aventura
- Ubuntu 16.0/18.04


#### Debian

This instruction applies to `Ubuntu 16.04/18.04`, `Debian 8/9` and Rio OS Aventura.

```

sudo apt-add-repository "deb [arch=amd64] https://get.rioos.xyz/repo/rioos/aventura/2.0.0-rc3/testing aventura testing"

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611

sudo apt-get update

sudo apt-get install -y rioos-nodelet rioos-network


```

#### RedHat based

This instruction applies to CentOS 7.x.


```

sudo yum-config-manager --add-repo https://get.rioos.xyz/repo/centos/rioos_digital.repo

sudo yum-config-manager --enable rioos_digital\*

sudo yum update

sudo yum install -y rioos-nodelet rioos-network

```

Now, You have to successfully Installed nodelet.

### Storage

The following operating systems are supported. 
 
- Debian  8/9
- CentOS 7.x
- Rio OS Aventura
- Ubuntu 16.0/18.04


#### Debian

This instruction applies to `Ubuntu 16.04/18.04`, `Debian 8/9` and Rio OS Aventura.

```

sudo apt-add-repository "deb [arch=amd64] https://get.rioos.xyz/repo/2.0/ubuntu/16.04/testing aventura testing"

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611

sudo apt-get update

sudo apt-get install -y rioos-storelet rioos-network

```

#### RedHat based

This instruction applies to CentOS 7.x.

```

sudo yum-config-manager --add-repo https://get.rioos.xyz/repo/centos/rioos_digital.repo

sudo yum-config-manager --enable rioos_digital\*

sudo yum update

sudo yum install -y rioos-nodelet rioos-network

```

Read [Detail storage guide](/storages) to configure and use the storage.

## Datacenter

Now that the basic constructs are setup, its time to setup the datacenter. 

The taks that are needed are

*   Connect Compute
*   Create Storage and mount disks
*   Configure Networking (subnets)
*   Create Datacenter and attach compute nodes, storage and netoworking.

Read [Detail datacenter guide](/datacenters) to configure and use the storage.


