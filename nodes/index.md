---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Nodes
description: This section provides information on onboarding Nodes and managing them.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Datacenters
        url: '/datacenters/index.html'
    next:
        content: Networks
        url: '/networks/index.html'
---

## Nodes

Nodes are the basic element in Rio OS. They provide the basic ingredient - [CPU/GPU, RAM, DISK) for a cloud operating system.

### Nodelet

Nodes are managed by `Nodelet`. Nodelet is an agent that manages the digitalcloud, containers, blockchain apps in the baremetal node.

### Pre reqs

You must have completed [installation of nodelet](/docs/getting_started/installing).

### Configuration

> The configuration `nodelet.rioconfig` is automatically created during [installation](/docs/getting_started/installing)

<div class="callout callout--info">
    <p><strong>Changing configuration</strong>There is no need to change the `nodelet.rioconfig` as it is automatically created with strong encryption.</p>    
</div>


### Running


``` 


sudo systemctl start rioos_nodelet

sudo systemctl status ioos_nodelet


```

To tail the logs of the nodelet

```

sudo journalctl -u rioos_nodelet.service -f

```

### Register

The nodes are registered into Rio OS automatically with the `hostname` and an unique `machine id` with the flag `Scheduled` true or false. 

### Configuration

- Change the smtp host 

```

nano /var/lib/rioos/context/init.sh


``` 

- Change the slacktoken

```

nano /var/lib/rioos/context/init.sh


``` 

- Copy the gulp.rioconfig from /var/lib/rioos/config to /var/lib/rioos/context

```

cp /var/lib/rioos/config/gulp.rioconfig /var/lib/rioos/context


``` 

- Change the log storage (InfluxDB) in fluent-bit.conf

```

nano /var/lib/rioos/context/fluent-bit.conf


``` 


### Scaling

To scale nodes, repeat the registration in another node 

- Copy the `/var/lib/rioos/config/nodelet.rioconfig` 

- Perform the [installation](/docs/getting_started/installing)


### Verify

**CLI**

Watch [asciinema](/docs/cli) to list nodes.

**UI**

**Login**  [command center](/docs/command_center)

> In the Dashboard, the registered node appears in a few seconds. 

In this case there are 2 registered nodes.

![Nodes](/docs/doks-theme/assets/images/infra/snapshot_nodes.png)
