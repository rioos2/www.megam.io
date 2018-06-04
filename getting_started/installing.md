---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Install
description: This section covers the standard procedure to install Rio/OS 2.0 *Aventura* using an ISO and an alternative manual method in an existing OS.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Getting Started
        url: '/getting_started'
    next:
        content: Command Center
        url: '/command_center/index.html'
---

## Install

Rio/OS offering two types of installation 

- Bootable USB Stick.
- Existing OS using native packages (deb, rpm) and docker containers.


### What is installed ?

The Rio OS components are grouped as per the pic.

![Rio/OS Components](/docs/doks-theme/assets/images/RIO_OS_Master_Software.png)


<table>
  <tr>
   <td>Name
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>Command center
   </td>
   <td>Command center for Rio/OS
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
   <td>Persistent storage
   </td>
  </tr>
  <tr>
   <td>API Server
   </td>
   <td>API for Rio/OS. The heart of the system which acts as the mediator for all of the  Rio/OS system components.
   </td>
  </tr>
  <tr>
   <td>Telemetry
   </td>
   <td>Metrics collector and analytics for Rio OS 
   </td>
  </tr>
  <tr>
   <td>PowerDNS
   </td>
   <td>Assign domain names for Rio/OS (Base Rio, digital cloud, containers and blockchain-backed apps)
   </td>
  </tr>
  <tr>
   <td>Machine Console
   </td>
   <td>A VNC console proxy to access digital cloud
   </td>
  </tr>
  <tr>
   <td>Blockchain
   </td>
   <td>Events storage based on blockchain.
   </td>
  </tr>
  <tr>
   <td>Nodelet
   </td>
   <td>Rio OS compute enabler. Runs on nodes which will provide compute.
   </td>
  </tr>
  <tr>
   <td>Fluent Bit
   </td>
   <td>Logs collector
   </td>
  </tr>
  <tr>
   <td>Storlet
   </td>
   <td>Rio OS storage enabler. Runs on nodes that provides storage.
   </td>
  </tr>
</table>


![Rio/OS Hub and Spoke](/docs/doks-theme/assets/images/RIO_OS_Hub_Spoke.png)

## Master

**A Master contains the core Rio OS components.**

*   Command Center
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
*   Fluent Bit


## Storage

Digital cloud, container and blockchain apps consume space from storage server. 

**A Storage component.**

*   Storlet

### Option 1: ISO Installation

ISO is packed with Rio OS components that is sufficient to make a private cloud environment.

<div class="callout callout--warn">
    <p><strong>Request access</strong>Contact sales@rio.company for requesting access to the private link.</p> 
</div>

Download the ISO from [the private link here](https://drive.google.com/drive/u/1/folders/1Be88vR2NjywQfE_cDN4-ge0x9U8V2SWa){:target="_blank"}. Burn the ISO into the USB using your platform specific instructions.

<div class="callout callout--info">
    <p><strong>Installing!</strong> Insert the USB in the server. Follow the instructions and you are done.</p> 
</div>


## Option 2: Autorio:  Recommended

Rio/OS comes packaged as a combination of native debs/rpm packages and  docker containers stored in a  private registry.

### Pre requistes


<div class="callout callout--info">
    <p><strong>Pre requisites</strong>Ruby 2.5.x installed in your workstation.</p> 
</div>


### Install 

Visit [Autorio](https://github.com/rioadvancement/autorio) for detailed instruction.


### Rollback

Visit [Autorio](https://github.com/rioadvancement/autorio) for detailed instruction.



## Option 3: Manual

Rio/OS comes packaged as a combination of native debs/rpm packages and  docker containers stored in a  private registry.

### Planning

Every site has its own ip addresses. Hence a common set of variables are exported before the install.


<div class="callout callout--info">
    <p><strong>Caution</strong>exported variables are persistent in your current bash terminal only. If you open another terminal then perform the export again in the new terminal.</p> 
</div>



```
export MY_IP_ADDRESS=192.168.2.47

export RIOOS_VERSION=2.0.0.rc4

export RIOOS_REPO=get.rioos.xyz

export RIOOS_REGISTRY=registry.rioos.xyz:5000

export RIOOS_HOME=/var/lib/rioos

export RIOOS_CONFIG_HOME=$RIOOS_HOME/config

export DNS_ENDPOINT=http://console.rioos.xyz:8081

export API_SERVER=https://console.rioos.xyz:7443

export WATCH_SERVER=https://console.rioos.xyz:8443

```

### Install Docker 

#### Debian based

```

sudo apt-get install wget curl

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs) stable"

sudo apt-get update -y

sudo apt-get install -y docker-ce

```

#### RedHat based

```

sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
    
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo

sudo yum install docker-ce

```

Elevate `docker user` to `sudoer`. Helps not to type `sudo docker <command>` for all the commands.


```
sudo usermod -aG docker ${USER}
```


#### Run Docker


```
sudo systemctl start docker

sudo systemctl status docker
```

#### Access Private Registry

<div class="callout callout--warn">
    <p><strong>Request access</strong>Contact sales@rio.company for requesting access to the private registry  CA certificate.</p> 
</div>

Contact [sales](mailto::sales@rio.company) requesting access to the below link.

#### Download the private registry CA certificate

The [CA certificate](https://drive.google.com/open?id=1s43DatiJHgbdXNdlcc8TYYW0AlA3vLIL) is needed to access the private registry behind TLS.

### Create /etc/docker/certs.d

Copy the downloaded `ca.crt` into `/etc/docker/certs.d/$RIOOS_REGISTRY` directory


```
sudo -s

export CA_CRT=$PWD/ca.crt

mkdir -p /etc/docker/certs.d/$RIOOS_REGISTRY

mv $CA_CRT /etc/docker/certs.d/$RIOOS_REGISTRY

exit

```

#### Login to registry


```

docker login $RIOOS_REGISTRY

userid: rioosadmin    
password: team4rio 

```


### Add Debian based Repo

Add *deb testing* packaging repo using the instructions below in systems running `Rio OS Aventura`, `Ubuntu 16.04/18.04` and `Debian 8/9`.

```

sudo apt-add-repository "deb [arch=amd64] https://$RIOOS_REPO/repo/rioos/aventura/$RIOOS_VERSION/testing aventura testing"

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 02789828

sudo apt-get update


```

### Add RedHat based Repo

Add *yum testing* packaging repo using the instructions below in systems running `CentOS 7.x`.


```

cat << EOT > /etc/yum.repos.d/rioos.repo
[RioOS]
name=RioOS
baseurl=https://$RIOOS_REPO/repo/centos/centos7/$RIOOS_VERSION/testing/centos7/
enabled=1
gpgcheck=0
EOT

sudo yum update


```


### Install Master

After successfully accessing the Rio/OS private registry. 

<div class="callout callout--info">
    <p><strong>Master IP Address</strong><code class="highlighter-rouge">$MY_IP_ADDRESS</code> contains the master ip address. In this case <code class="highlighter-rouge">192.168.2.47</code>. Replace it with the ip address of your server.
    </p>    
</div>

<div class="callout callout--info">
    <p><strong>Version</strong>2.0.0-rc3 is the latest version referenced as $RIOOS_VERSION. Verify the release notes for newer versions.</p>    
</div>

<div class="callout callout--warn">
    <p><strong>Environment Variables</strong>
    <ul>
    <li><code class="highlighter-rouge">$DNS_ENDPOINT</code> contains the PowerDNS endpoint. In this case <code class="highlighter-rouge">http://console.rioos.xyz:8081</code>. Replace it with your ip address of your dns endpoint.</li>
    <li><code class="highlighter-rouge">$API_SERVER</code> contains the Rio OS API Server endpoint. In this case <code class="highlighter-rouge">https://console.rioos.xyz:7443</code>. Replace it with your api server's endpoint.</li>
    <li><code class="highlighter-rouge">$WATCH_SERVER</code> contains the Rio OS Watch Server (http2 based) endpoint. In this case <code class="highlighter-rouge">https://console.rioos.xyz:8443</code>. Replace it with your watch server's endpoint.    
    </li>
    </ul>
    </p>    
</div>

*   Command center for Rio/OS.

```

sudo docker run -d -p $MY_IP_ADDRESS:443:8000 --name=rioosui_$RIOOS_VERSION -v $RIOOS_CONFIG_HOME:$RIOOS_CONFIG_HOME --restart always $RIOOS_REGISTRY/rioosui:$RIOOS_VERSION

```

*   Controller & Scheduler

```

sudo docker run -d --net=host -p $MY_IP_ADDRESS:10252:10252 --name=riooscontroller_$RIOOS_VERSION -e DNS_ENDPOINT=$DNS_ENDPOINT -e API_SERVER=$API_SERVER -e WATCH_SERVER=$WATCH_SERVER -v $RIOOS_CONFIG_HOME:$RIOOS_CONFIG_HOME --restart always $RIOOS_REGISTRY/riooscontroller:$RIOOS_VERSION


sudo docker run -d --net=host -p $MY_IP_ADDRESS:10251:10251 --name=rioosscheduler_$RIOOS_VERSION -e API_SERVER=$API_SERVER -e WATCH_SERVER=$WATCH_SERVER -v $RIOOS_CONFIG_HOME:$RIOOS_CONFIG_HOME --restart always $RIOOS_REGISTRY/rioosscheduler:$RIOOS_VERSION

```


*   PostgreSQL

This is used to store all Rio/OS data and DNS records


```

sudo docker run -d --name postgresql -e POSTGRES_PASSWORD=supersecret -v $RIOOS_HOME/pg-data:/var/lib/postgresql --restart always $RIOOS_REGISTRY/rioospostgres:10.3


```


*   API Server

Heart of Rio/OS. This is an Intermediary to the UI, controller, scheduler, nodelet and storlet. 


```

sudo docker run --net=host -d --name rioosapiserver_$RIOOS_VERSION -p $MY_IP_ADDRESS:7443:7443 -p $MY_IP_ADDRESS:8443 -p $MY_IP_ADDRESS:9443:9443 -e RIOOS_HOME=$RIOOS_HOME/ -v $RIOOS_CONFIG_HOME=$RIOOS_CONFIG_HOME --restart always $RIOOS_REGISTRY/rioosapiserver:$RIOOS_VERSION


```

*   Blockchain Events Server

```

sudo docker run -d --name rioosblockchain_$RIOOS_VERSION -p $MY_IP_ADDRESS:7000:7000 -v $RIOOS_CONFIG_HOME:$RIOOS_CONFIG_HOME -v $RIOOS_HOME/blockchain:$RIOOS_HOME/blockchain --restart always $RIOOS_REGISTRY/rioosblockchain:$RIOOS_VERSION


```


*   Telemetry

This is used to pull metrics for all digital cloud, containers, blockchain-backed apps, nodes.


```

sudo docker run -d --net=host -p $MY_IP_ADDRESS:9090:9090 --name rioosprometheus_$RIOOS_VERSION -v $RIOOS_CONFIG_HOME:$RIOOS_CONFIG_HOME  --restart always $RIOOS_REGISTRY/rioosprometheus:$RIOOS_VERSION

```


*   PowerDNS

Assign domain name to Rio/OS components, digital cloud, containers and blockchain-backed apps deployed by Rio/OS.

<div class="callout callout--warn">
    <p><strong>Pre requisites</strong>
    <ul>
    <li>
    postgresql container is available and running..
    </li>
    <li>
    <p>Make sure <code class="highlighter-rouge">jq</code> package for your operating sytem is installed.</p>
    <p>Debian based: <b>sudo apt-get install jq</b></p>
    <p>RedHat based: <b>sudo yum install -y jq</b></p>
    </li>
    </ul>
    </p>    
</div>

`AUTOCONF` environment variable is defined to use`PostgreSQL` backed database for PowerDNS.

```

sudo docker run -d --name rioospowerdns --link postgresql:postgresql -p $MY_IP_ADDRESS:8081:8081 -p $MY_IP_ADDRESS:53:53 -p $MY_IP_ADDRESS:53:53/udp -e AUTOCONF=postgres -e PGSQL_USER=postgres -e PGSQL_PASS=supersecret --restart always $RIOOS_REGISTRY/rioospowerdns:4.0.3 --cache-ttl=120 --allow-axfr-ips=127.0.0.1


```

*Create a private domain named rioosbox.com in PowerDNS*


```bash

curl -X POST --data '{"name":"rioosbox.com.", "kind": "Native", "masters": [], "nameservers": ["ns1.rioosbox.com.", "ns2.rioosbox.com."]}' -v -H 'X-API-Key: rioos_api_key' http://$DNS_ENDPOINT/api/v1/servers/localhost/zones | jq .

```

*Verify rioosbox.com*

```bash

curl -H 'X-API-Key: rioos_api_key' $DNS_ENDPOINT/api/v1/servers/localhost/zones | jq .

```

* Logs Collector

Fluent Bit is used to collect logs from nodes, digitalcloud, containers and blockchain-backed apps. 


* Logs Storage plugin - InfluxDB 

This is a logs storage for Fluent Bit. All logs collected gets stored in influxDB


```

sudo docker run -d -p $MY_IP_ADDRESS:8086:8086 --name=influxdb -v $RIOOS_HOME/influxdb:$RIOOS_HOME/influxdb --restart always $RIOOS_REGISTRY/rioosinfluxdb:1.3.7

```


* Logs Storage plugin - Elastic Search

Yet another logs storage for Fluent Bit.

```

docker run -d r$RIOOS_REGISTRY/riooselasticsearch:5.6.9

```

* Visualize Logs for Elastic Search using Kibana.

Here the elastic search's ip address is `172.17.0.2` 

```

docker run --name kibana -e ELASTICSEARCH_URL=http://172.17.0.2:9200 -p 5601:5601 -d $RIOOS_REGISTRY/riooskibana:5.6.9

```

* Visualize Logs for InfluxDB using Chronograf

```
docker run -p 8888:8888 $RIOOS_REGISTRY/riooschronograf:1.3.10.0

```


* Machine console server

The following operating systems are supported. 
 
- Debian  8/9
- CentOS 7.x
- Rio OS Aventura
- Ubuntu 16.0/18.04


#### Debian based


[Add Debian based repo](#add-debian-based-repo) must be addded before attempting an install.


```

sudo apt-get install -y rioos-vnc


```

#### RedHat based

[Add RedHat based repo](#add-redhat-based-repo) must be added before attempting an install. 


```

sudo yum install -y rioos-vnc

```


### Instal Nodelet

Nodelet is installed in every compute node. 

The following operating systems are supported. 
 
- Debian  8/9
- CentOS 7.x
- Rio OS Aventura
- Ubuntu 16.0/18.04


#### Debian

[Add Debian based repo](#add-debian-based-repo) must be addded before attempting an install.

```

sudo apt-get install -y rioos-nodelet


```

#### RedHat based

[Add RedHat based repo](#add-redhat-based-repo) must be added before attempting an install. 


```

sudo yum install -y rioos-nodelet

```

See [Nodes guide](/docs/nodes) to configure and use the nodes

### Storage

The following operating systems are supported. 
 
- Debian  8/9
- CentOS 7.x
- Rio OS Aventura
- Ubuntu 16.0/18.04


#### Debian based

[Add Debian based repo](#add-debian-based-repo) must be addded before attempting an install.

```

sudo apt-get install -y rioos-storlet

```

#### RedHat based

[Add RedHat based repo](#add-redhat-based-repo) must be added before attempting an install. 

```

sudo yum install -y rioos-storlet

```

Read more about [Storage](/docs/storages) to configure and use the storage.

## Location

Now that the basic constructs are setup, its time to setup a location. 

The taks that are needed are

*   Connecting Compute
*   Create Storage and mount disks
*   Configure Networking (subnets)
*   Create Datacenter and attach compute nodes, storage and netoworking.

Read more about [Locations](/docs/datacenters) to configure and use the datacenter.


