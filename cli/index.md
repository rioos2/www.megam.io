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
        url: '/command_center/index.html'
    next:
        content: Datacenters
        url: '/datacenters/index.html'
---

## CLI

Command line interface for Rio/OS.

<div class="callout callout--warning">
    <p><strong>Supported platforms </strong> Linux.</p>
</div>

### Installation

Go to [Rio OS CLI releases](https://github.com/rioadvancement/rioos/releases){:target="_blank"}

Download  the latest. 

```
mkdir $HOME/bin

wget https://github.com/rioadvancement/rioos/releases/download/2.0.0-rc3/rioos_20180427132544_Linux_amd64.tar.gz

tar -xf rioos_*_Linux_amd64.tar.gz -C $HOME/bin

rm rioos_*_Linux_amd64.tar.gz

```

#### Configuration cli.toml

Create a file `$HOME/.rioos/etc/cli.toml`

<div class="example">
    $HOME/.rioos/etc/cli.toml
</div>
```
api_server="https://console.rioos.xyz:7443"
email=
auth_token=
```

Where `api_server` is your site's  Rio OS API endpoint.

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

asciicinema illustrates deploying a digitalcloud
<div class="example">    
</div>
{% asciinema_play 175777 %}


#### List DigitalCloud

<div class="example">    
</div>
{% asciinema_play 174766 %}

#### Deploy a container: Jenkins

<div class="example">    
</div>
{% asciinema_play 175811 %}


#### Deploy a container: Nginx and scale horizontally

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

This section is for administrators in managing the infrastructure using Rio OS.

#### Create Datacenter

asciinema illustrates creating a datacenter
<div class="example">    
</div>
{% asciinema_play 174766 %}


#### List Datacenters

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

#### List Images

<div class="example">    
</div>
{% asciinema_play 174766 %}

#### List Jobs

<div class="example">    
</div>
{% asciinema_play 174766 %}







