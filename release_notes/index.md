---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Release Notes
description: v2.0 Release history

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Home
        url: '/'
---


## 2.0.0-rc8 : June 01, 2018 *upcoming

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc4?title=2.0.0.rc8){:target="_blank"}

*Features - tentative*

- Document CI/CD with sample git projects.

- Document Horizontal scaling/Vertical scaling with samples.

- Self healing - using node controller which updates the states of the node periodically.

- Blockchain backed apps using hyperledger fabric/chaincode.


## 2.0.0-rc7 : May 25, 2018

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc4?title=2.0.0.rc7){:target="_blank"}

*Features*

- UI Infrastructure with options to edit location, virtual network.

- Performance testing of Rio/OS using [rioosperf using locust.io](https://github.com/rioadvancement/rioosperf){:target="_blank"}

- Find the bottlenecks in preformance of telemetry processor with an assumption of 100 users (50k http requests per second)

- Test the recoverable states of containers.

- Stability testing and fixes for scheduler to process jobs correctly.

- Push the containers built into a private registry and process continious deploy - Good case.

## 2.0.0-rc6 : May 18, 2018

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc4?title=2.0.0.rc6){:target="_blank"}

*Features*

- Install Rio/OS using [autorio](https://github.com/rioadvancement/autorio){:target="_blank"}

- UI Infrastructure - preview.

- Notification mailers moved to api server.

- Horizontal scaler numbers new instances with incremental numerics

- Nodelet when restarted brings up the state of digitalcloud, container to the last known state.


## 2.0.0-rc5 : May 11, 2018

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc4?title=2.0.0.rc5){:target="_blank"}

*Features*

- CLI perform CI/CD using BuildConfig.

- CLI perform clean logout by wiping off the device session.

- Launch containers from private registry 

- Dashboard metrics - statistics of node' process metrics/disk IO.

- Nodelet keeps upto date status of containers/VM by probing them periodically.

## 2.0.0-rc4 : May 04, 2018

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc4?title=2.0.0.rc4){:target="_blank"}

*Features*

- User login from devices are tracked with multi sessions.
- Node statistics charts of disk usage.
- Node statistics network speed usage  selection themed.
- Mailers for running, security are themed.
- Qemu when resized images using unit string "M" instead of "MiB" in Ubuntu 18.04

## 2.0.0-rc3 : April 27, 2018

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc31?title=2.0.0.rc3.1){:target="_blank"}

*Features*

- An operational view of Rio/OS with their status 

## 2.0.0-rc1 : April 13, 2018

- [Bugs Fixed](https://gitlab.com/groups/rioos/-/milestones/200rc13?title=2.0.0.rc1.3){:target="_blank"}

*Features*

- Datacenters

Create locations and manage them. See [Datacenters](../datacenters) for more details.

- Command Center

UI to manage your datacenter. See [Command Center](../command_center) for more details.


- Scaling

Scale apps based telemtry criteria. See [Scaling](../scaling) for more details.

- Digital Cloud, Container

Deploy a digital cloud, container. [Command Center](../command_center) and [Quick Starters](../quick_starters)


- Security

PKI (public key infrastructure) provides a strong security across Rio OS. Refer [Security](../security)

- Identity & Access

Support for authentication using Password, Token, JWT, Passticket. See [security](../security)

- Rio.Market

Headless API that supports a curated list of applications. Sync curated apps from Rio.Marketplace into Rio OS.

- CLI


### Mind map Rio OS v2.0.0


![Mind map Rio OS](/docs/doks-theme/assets/images/RIO_OS_XMind.jpg)
