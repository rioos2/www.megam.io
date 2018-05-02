---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Audits, Centralized Log and Monitoring (Telemetry)
description: Auditing events, logging and what do we monitor

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Scaling
        url: '/scaling'
    next:
        content: Quick Starters
        url: '/quick_starters'
---

## Audits 

Audits are backed by rock solid immutable layer.  Audit events for an user is show in the command center. Actions performed on Rio OS can be audited. This allows a full administrator to ensure that system tasks are being appropriately performed. This potentially facilitates compliance with regulatory standards.

The records created by the Rio OS Auditing facililty capture information on who has performed what action, when, and how successfully:

**Who:** The administrator performing actions. To access the system, each administrator has authenticated, either locally or by and is therefore identifiable throughout their session.

**What:** The action performed. 30 different kinds of action are tracked by Rio OS.

**When:** The UTC time stamp that corresponds to each recorded action.

**How:** The success or failure of the action.

Audit records are created by Rio OS API Server, which run asynchronously. Each record is stored as a JSON, which can be retrieved and inspected.


### List of Audit Events

Events audited by Rio OS include successful and failed logins, events associated with deployment and the use of tools that require administrative privileges. Corresponding information is captured in the output immutable layer.

|                                              |                                |                                       |
|----------------------------------------------|--------------------------------|---------------------------------------|
| Login succeeded or failed                    | Audit configuration changed    | Auditing enabled or disabled          |
| Node added to cluster                        | Node removed from cluster      | Node failed over                      |
| Storage added to cluster                     | Storage removed to cluster     | Cluster rebalanced                    |
| System started or shut down                  | Digital Cloud  created         | Digital Cloud deleted                 |
| Digital Cloud action start/stop/reboot   | Container  created             | Container  deleted                    |
| Container action start/stop/reboot       | Blockchain App  created        | Blockchain App deleted                |
| Blockchain App action start/stop/reboot  | User added                     | User deleted                          |
| Password changed or reset                    | Role added                     | Role deleted                          |
| Role failed - Unauthorized <RESOURCE>.<VERB> | Security keys created for user | Security keys accessed - DigitalCloud |
| Security key access failed - DigitalCloud    | Console accessed - Container   | Console accessed - DigitalCloud       |

## Telemetry

Rio Telemetry performs service discovery of the digital cloud, containers, nodes, storages and reports metrics. 

The metrics collected gets manifested in the [Command Center](../command_center)


### Centralized Logging

Admins need centralized logging ability to skim through logs and analyze them. There needs to be ability for users to look at their logs of their deployment. 

![Centralized Logging](/docs/doks-theme/assets/images/audit/RIO_OS_Centralized_Logging.png)


#### Collector 

Fluentbit will be run on every node and inside the digitalcloud. 

Fluentbit collects logs and outputs them to one or more endpoints.  

The output plugins supported are 

- Elastic search
- InfluxDB
- Https endpoint


Kibana provides  ability to display logs, If ElasticSearch is configured as the output plugin.

Chronograph provides ability to display logs, If InfluxDB is configured as the output plugin. 

#### Locations

| Log Type        | Files                                                                                | Sym Link                                                                    |
|-----------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Digital Cloud   | /var/log/libvirt/qemu/<rioos.deploy_domain.name>.log                                 | /var/lib/rioos/logs/machines/<account-id>/<assembly-id>/<machine_uid>.log   |
| Containers      | /var/lib/docker/container/:container_id/*.log                                        | /var/lib/rioos/logs/containers/<account-id>/<assembly-id>/<machine_uid>.log |
| Blockchain Apps | /var/lib/docker/container/:container_id/*.log                                        | /var/lib/rioos/logs/containers/<account-id>/<assembly-id>/<machine_uid>.log |
| Rio OS          | /var/log/rioos/**.logs  /var/lib/docker/container/<rioos_specific_container/logs     |                                                                             |


#### Installation

- Fluentbit
- InfluxDB



