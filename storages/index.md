---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Storages
description: Page description

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Networks
        url: '../../networks/index.html'
    next:
        content: Security
        url: '../../security/index.html'
---

## Storages

Storages the basic ingredient - [DISK) for a cloud operating system. 

### Storlet

Storages are managed by `Storlet`. Storlet is an agent that manages the storage for  digitalcloud, containers, blockchain apps.

### Installation

#### Clean Install

Boot the node with [USB (Rio OS ISO)](/install#iso) and follow the options prompted.

####  Existing Rio OS node

```


sudo apt-add-repository "deb [arch=amd64] https://registry.rioos.xyz/repo/rioos/aventura/2.0.0-rc1/testing  aventura testing"

sudo apt-get -y update

sudo apt-get install rioos-storlet


```

### Configuration

> The configuration `storlet.rioconfig` exists as created during [installation](/getting_started/installing)

<div class="callout callout--info">
    <p><strong>Changing configuration</strong>There is no need to change the `storlet.rioconfig` as it is automatically created with strong encryption.</p>    
</div>


### Running


``` 


sudo systemctl stop rioos_storlet

sudo systemctl start rioos_storlet


```

To tail the logs of the storlet

```

sudo journalctl -u rioos_stor.service -f

```

### Register

The storlet registers a local storage from the node its running automatically into Rio OS if it doesn't find the supported storage types. 

To repeat the registration in another node

- Copy the `/var/lib/rioos/config/storlet.rioconfig` 
- Perform the installation

You will see the additional storages displayed in the [command center](/command_center)