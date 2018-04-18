---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: CLI
description: This section provides information to use the rioos cli

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
    <p><strong>Supported platforms</strong> Linux 64 bit.</p>
</div>

### Installation

Go to [rioos cli releases](https://github.com/rioadvancement/rioos/releases)

Download  the latest. 

```
mkdir $HOME/bin

wget https://github.com/rioadvancement/rioos/releases/download/2.0.0-rc1/rioos_20180409063706_Linux_amd64.tar.gz

tar -xf rioos_20180409063706_Linux_amd64.tar.gz -C $HOME/bin

rm rioos_20180406103819_Linux_amd64.tar.gz

```

#### cli.toml

Create `$HOME/.rioos/etc/cli.toml`

<div class="example">
    $HOME/.rioos/etc/cli.toml
</div>
```
api_server="https://console.rioos.xyz:7443"
email=
auth_token=
```

`api_server` is the Rio OS site api endpoint.

### Commands 

####  Identity

**Signup with Rio OS**


```

$ rioos cli new

```

**Login to Rio OS**


```

$ rioos login

```
Upon successful login, `rioos` updates $HOME/rioconfig/cli.toml with 


**Logout of Rio OS**

```

rioos logout

```

Upon successful login, `rioos` updates $HOME/rioconfig/cli.toml with 


#### Datacenter


<div class="example">
    TEST
</div>
{% asciinema_play 174766 %}


#### Deploy Digitalcloud

<div class="example">
    TEST
</div>
{% asciinema_play 175777 %}


#### Deploy a container: Jenkins

<div class="example">
    TEST
</div>
{% asciinema_play 1757811 %}


#### Deploy and scale

<div class="example">
    TEST
</div>
{% asciinema_play 174766 %}


#### Deploy and scale horizontally blockchain apps


- Images list (list of all plans)

- Nodes list

- Datacenters list 

- Storages list

- Digitalcloud deploy list

<div class="example">
    TEST
</div>
{% asciinema_play 174766 %}




