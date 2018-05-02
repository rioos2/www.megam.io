---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Storages
description: This section provides overview on supported storages and its consumption in Rio OS.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Virtual Networks
        url: '/networks/index.html'
    next:
        content: Security
        url: '/security/index.html'
---

## Storages

Storages the basic ingredient - [DISK) for a cloud operating system. The storage plugins supported in Rio OS are 

- Local
- NFS
- Ceph

The storage plugins are easily extendable.

### Storlet

Storage is managed by `Storlet`. Storlet is an agent that manages the storage for  digitalcloud, containers, blockchain-backed apps.

Storlet uses storage plugin to integrate any storage of bare metal server with Rio OS.

### Pre reqs

You must have completed [installation of storlet](/docs/getting_started/installing).

### Configuration

> The configuration `storlet.rioconfig` is automatically created during [installation](/docs/getting_started/installing)

<div class="callout callout--info">
    <p><strong>Changing configuration</strong>There is no need to change the `storlet.rioconfig` as it is automatically created with strong encryption.</p>    
</div>


### Installation


``` 

sudo systemctl stop rioos_storlet

sudo systemctl start rioos_storlet


```

To tail the logs of the storlet

```

sudo journalctl -u rioos_storlet.service -f

```

### Storage Plugins

**Local**

Local plugin is turned on by default. Storlet automatically registers the node it runs to be consumed as storage.


**NFS**

NFS plugin is turned on if storlet detects the presence of `nfs-server`. Storlet automatically registers the node it runs to be consumed as NFS storage.


**Ceph**

Ceph plugin is turned on if storlet detects the presence of `ceph-deploy`. Storlet automatically registers the node it runs to be consumed as Ceph storage.


To scale storage, repeat the registration in another node 

- Copy the `/var/lib/rioos/config/storlet.rioconfig` 

- Perform the [installation](/docs/getting_started/installing)

### Storage Pool

A partitioned storage space served by a storage plugin.  As many partitioned storage space can be created inside a storage served by the plugin limited to the availability of disk space.

### Verify

**CLI**

Watch [asciinema](/docs/cli) to list storages.

**UI**

**Login**  [command center](/docs/command_center)

Click **Settings** > **Infrastructure** 

Click **Storages**

In this case there is one registered storage using NFS plugin.

Click **Create Pool** > from the right side

![Registered Storage](/docs/doks-theme/assets/images/infra/create_storagepool.png)

In this case there are two registered storages using NFS plugin with two storage pools.

![Registered Storage Pool](/docs/doks-theme/assets/images/infra/create_storagepool_done.png)