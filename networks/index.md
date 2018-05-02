---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Virtual Networks
description: Rio OS virtual networks allows applying networking to any node. Read below to configure/setup a virtual network.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Nodes
        url: '/nodes/index.html'
    next:
        content: Storages
        url: '/storages/index.html'
---

## Virtual Networks


Virtual Network enables a data center to provision the most suitable and efficient networking structure for the applications it hosts. And to alter that structure as conditions warrants, using software rather than requiring physical changes in connections to hardware.


![Rio/OS Virtual Network](/docs/doks-theme/assets/images/Rio_OS_Virtual_Network.png)


Nodes have the actual bridges setup with physical network attached. Rio OS connects to virtual networks via API for setting up networking to cloud workloads. 


### Installation

Every node needs the software and bridge network to be setup.

**A sample Ubuntu `/etc/network/interfaces`**

In this example a bridge `riopub` is attached to physical port `eth0`.

```

nano /etc/network/interfaces

```

Copy & Paste the following.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto riopub
iface riopub inet static
	address 107.152.143.242
	netmask 255.255.255.248
	network 107.152.143.240
	broadcast 107.152.143.247
	gateway 107.152.143.241
	# dns-* options are implemented by the resolvconf package, if installed
	bridge_ports eno1
	bridge_stp off
	bridge_fd 0
	bridge_hello 2
	bridge_maxage 1
	dns-nameservers 8.8.8.8


```

Save File using CTRL + X and then Y

Create a bridge and reboot system

```

sudo brctl addbr riopub && sudo reboot

```

### Create Virtual Network

You must have the `Netmask`, `CIDR` and `Gateway`.

Rio OS automatically ignores the  first IP and the last IP in the CIDR range. 

```
Example:

Netmask = 255.255.255.248
Gateway = 107.152.143.241
CIDR = 107.152.143.240/29

The ip [107.152.143.240] is used as Network
The ip [107.152.143.241] is used as Gateway
The ip [107.152.143.242] is used as the node
The ip [107.152.143.247] is used as broadcast

Hence the usable ips are [107.152.143.243 - 107.152.143.246]
```

**CLI**

Refer [Asciicast in cli](/docs/cli). 

**UI**


Click > **Networks** > **Create**

![A cluster of nodes with private and public networking/local storage grouped in Location NEWYORK 01](/docs/doks-theme/assets/images/infra/create_network.png)


Click > **Create**


The newly created virtual network is listed as below.

![A cluster of nodes with private and public networking/local storage grouped in Location NEWYORK 01](/docs/doks-theme/assets/images/infra/create_network_done.png)


Rio OS automatically manages used and unsed ips of a virtual network from the range provided for a node.

The newly created virtual network is ready for selection during creation of  [Datacenters](/docs/datacenters)


