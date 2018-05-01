---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: CLI
description: This section provides information to use the Rio OS cli

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Command Center
        url: '../../command_center/index.html'
    next:
        content: Datacenters
        url: '../../datacenters/index.html'
---

## CLI

Command line interface cli to manage Rio/OS.

<div class="callout callout--warning">
    <p><strong>Supported platforms </strong> Linux.</p>
</div>

### Installation

Go to [Rio OS CLI releases](https://github.com/rioadvancement/rioos/releases){:target="_blank"}

Download  the latest. 

```
mkdir $HOME/bin

wget https://github.com/rioadvancement/rioos/releases/download/2.0.0-rc3/rioos_20180427132544_Linux_amd64.tar.gz

tar -xf rioos_20180409063706_Linux_amd64.tar.gz -C $HOME/bin

rm rioos_20180406103819_Linux_amd64.tar.gz

```

#### Configuration cli.toml

Create `$HOME/.rioos/etc/cli.toml`

<div class="example">
    $HOME/.rioos/etc/cli.toml
</div>
```
api_server="https://console.rioos.xyz:7443"
email=
auth_token=
```

`api_server` is the Rio OS site's api endpoint.

###  Identity

#### Signup with Rio OS


```

$ rioos cli new

```

#### Login to Rio OS


```

$ rioos login

```

Upon successful login, `rioos` cli updates $HOME/rioconfig/cli.toml with the users  `account_id`, `token` and `email`.


#### Logout of Rio OS

```

rioos logout

```

### Deployment

#### Deploy a digitalcloud: Ubuntu

asciicinema illustrates creating a digitalcloud
<div class="example">    
</div>
{% asciinema_play 175777 %}


#### Deploy a container: Jenkins

<div class="example">    
</div>
{% asciinema_play 1757811 %}


#### Deploy a container: Nginx and horizontally scale

<div class="example">    
</div>
{% asciinema_play 174766 %}

#### List DigitalCloud

<div class="example">    
</div>
{% asciinema_play 174766 %}

#### Create Secret

<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Secret

<div class="example">    
</div>
{% asciinema_play 174766 %}

### Infrastructure

This section is for administrators who will setup, manage infratucture using Rio OS in their site.

#### Create Datacenter

asciinema illustrates creating a datacenter
<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Nodes

<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Storages

<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Networks

<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Jobs

<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Datacenters

<div class="example">    
</div>
{% asciinema_play 174766 %}

#### List Storages

<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Images

<div class="example">    
</div>
{% asciinema_play 174766 %}






