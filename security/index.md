---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Security & RBAC
description: This section provides information on Rio OS PKI infrastructure, different ways of  storing secret, and shielding authorization using roles/permissions.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Storages
        url: '/storages'
    next:
        content: Scaling
        url: '/scaling/index.html'
---

## Security

PKI, Public Key Infrastructure is a web of trust. When you are communicating with  multiple persons, which wants to mutually authenticate themselves (and their websites), you first choose a common trusted person. This third person becomes a "Trusted Third Party" and will be called the "Certificate Authority" (CA) for the purpose of certificate management.

The CA will create a master key, also known as root CA key. 

The private key will be kept secret by the Thirty part at all cost. 

The public key will be embedded into a certificate, and this certificate will be signed by the public key of the CA. 

This means the certificate is self-signed and you can verify the signature with the key inside it. 

![Security](/docs/doks-theme/assets/images/security/RIO_OS_Identity.png)


### PKI Infrastructure

Rio OS upon installation sets up a root CA key and certificates for each of the software to interoperate.

Rio/OS api server is the center funnel which mediates across all the systems in Rio/OS using a public/private key infrastructure.

The certificates are stored in `/var/lib/rioos` and embedded in the respective `.config` files.

### Identity

The authentication supported in Rio OS are 

- Password
- Token
- JWT
- PassTicket
- SAML
- OpenID
- LDAP

#### Password

Input is a combination of email and password. A token is generated for verified users. 

This is used by the UI and CLI to verify login.

#### Token

Input is a combination of email and token. Tokens expires in a day. The token is refershed automatically upon expiration.

This is used by the UI, CLI to perform RESTful API calls.

#### JWT

Input is a JWT token generated from secret certificates known by the API server and the Rio OS system components.

This is used by Rio OS system software to perform RESTful API calls. Useful for system-system to communicate in a secure way.

#### PassTicket

Input is a onetime password token valid for single use. 

This is used by Rio OS system software to bootstrap with the API server (first time only). 


### Secrets

Rio OS has ability to store secrets like user generated certificates in a vault.

### RBAC

Role based access control.

Any role can be created with permissioned access. The access is restricted based on REST resource and its VERB. 

The default roles setup inside Rio OS are 

| Roles                  | Description                                                  | Permissions |
|------------------------|--------------------------------------------------------------|-------------|
| rioos:superuser        |  Superuser of RIO/OS. It has all powers of RIOOS system.     | `rioos.*.*`   |
| rioos:universalsoldier | Universalsoldier is system level user (like service account) |             |
| rioos:loneranger       | This is a regular user                                       |             |


#### Permissions 

A permission is denoted by `<system>:<REST resource>:<verb>`. A `<verb>` is HTTP REST based - GET, PUT, POST, DELETE or wildcard.

The permission for the built-in roles are

| rioos:superuser | rioos:universalsoldier                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | rioos:loneranger                                                                                                                                                                                                                                                                                                                                         |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rioos.*.*`       | rioos.assembly.get rioos.assembly.put rioos.assembly.delete rioos.assemblyfactory.get rioos.assemblyfactory.put rioos.assemblyfactory.delete rioos.serviceaccount.put rioos.serviceaccount.delete rioos.horizontalscaling.get rioos.horizontalscaling.put rioos.verticalscaling.get rioos.verticalscaling.put rioos.secrets.* rioos.endpoints.* rioos.jobs.* rioos.service.* rioos.volumes.* rioos.nodes.* rioos.storageconnectors.* rioos.storagepool.* rioos.settingsmap.* rioos.imagereferences.* rioos.imagemarks.* rioos.build.* rioos.buildconfig.get rioos.buildconfig.put rioos.plans.get rioos.plans.put rioos.accounts.get rioos.datacenters.get rioos.datacenters.put rioos.networks.get rioos.networks.put rioos.audits.post |  rioos.assembly.put rioos.assembly.get rioos.assemblyfactory.* rioos.horizontalscaling.* rioos.verticalscaling.* rioos.secrets.* rioos.endpoints.* rioos.service.* rioos.buildconfig.* rioos.logs.get rioos.audits.get rioos.volumes.get rioos.accounts.get rioos.accounts.put rioos.datacenters.get rioos.healthz.get rioos.plan.get rioos.networks.get |


****


### Origins


We need ability to isolate/sandbox users in Rio/OS. Origins helps to tantalize users to only access, manage in their private space.

![Origins](/docs/doks-theme/assets/images/security/RIO_OS_Origin_Teams.png)

Bigger organization where various groups are present with different requirements. Different departments/branches of a large enterprise firm can create organizations, invite people and grant permissions to access their applications that the department has launched

In the above picture, the **Rio**, **HNMC** are organizations. *Rio360*, *devrioos* are teams under organization *Rio*.  

Origin is essentially a group where an user who creates it has the default authority.

![Teams](/docs/doks-theme/assets/images/security/RIO_OS_Roles_Permission_Teams.png)

Origins have teams associated with it. Every user account is (optionally) associated to a team or origin.



