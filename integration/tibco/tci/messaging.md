---
title: Messaging
description: eFTL
published: true
date: 2021-05-18T10:44:07.387Z
tags: 
editor: markdown
dateCreated: 2021-05-17T07:47:30.293Z
---

# Messaging

## General Concepts

The TIBCO Cloud Messaging fully integrated communications solution provides system-to-system data distribution in fully managed cloud infrastructure.

![screen_shot_2019-05-02_at_2.38.23_pm.png](/screen_shot_2019-05-02_at_2.38.23_pm.png)

**Useful Links:**

Getting started with TIBCO Cloud™ Messaging: 
https://messaging.cloud.tibco.com/docs/getstarted

Getting Started with TIBCO Cloud™:
https://account.cloud.tibco.com/cloud/docs/index.html

Informations about TIBCO Cloud™ Messaging plans:
https://www.tibco.com/products/tibco-cloud-messaging/pricing-plans

## Getting Started

1. Log in to TIBCO Cloud™ Integration [https://cloud.tibco.com/] and select the region. 
2. Choose an organization with a tibco cloud messaging subscription,  then click on the hexagon labeled Messaging. 
3. TIBCO Cloud Messaging is structured in three main tabs, namely *Status*, *Downloads* and *Authentication Keys*, which allow you to use and manage all the features of this tool. 
### Status

The Status section allows you to check and get information about current connections, peak connections and total messages sent in the current month. In addition, the two URLs to be used respectively in eFTL and FTL applications are exposed.

>![tcmstatus.png](/tcmstatus.png) 
> *The TIBCO Cloud Messaging Status page; The green checkmark indicates that the Messaging subscription is active and running*

### Downloads

This page collects the TIBCO Cloud™ Messaging SDKs (Software Development Kits) for TIBCO eFTL™.

>![tcmdownloads.png](/tcmdownloads.png)

After having chosen a programming language among those available, start the download to obtain an archive file containing all the resources needed to code.

By clicking on the *Start coding*  link related to the language, you can consult a large number of dedicated tutorials. 
These tutorials require you to have a URL and an authentication key to make a connection. You'll find both on the Authentication Keys page.
### Authentication Keys

On the Authentication Keys page you can create authentication key objects that can be used to establish one or more connections to TIBCO Cloud Messaging. They then play the role of a special password associated with the URLs of the eFTL/FTL apps, which are shown at the top of the section (alternatively, these URLs of interest are also shown by selecting the Status tab).

Each authentication key can be used to create any number of connections, but it is recommended to separate them for each environment (*Develop*, *Test*, *Pre-Prod*, *Prod*, etc.).

>![tcmauthkeys.png](/tcmauthkeys.png)
> *The Authentication Keys page of TIBCO Cloud Messaging* 

> These authentication keys do not have any expiration date but there is a limit [10] on the maximum number of keys that can be built for each subscription.
{.is-info}


All the information needed to connect the clients to TIBCO Cloud Messaging are contained in a YAML file named ***tcm-config.yaml***, which is unique for each authentication key and can be simply downloaded by clicking on the arrow icon next to each key. In particular, the Cloud Messaging Client Configuration File contains the following essential fields:

- **tcm_authentication_id:** A unique identifier associated with tcm_authentication_key. Recommended to be set as the username for both eFTL and FTL when connecting with that key.
- 
- 
- **tcm_authentication_key:** A signed JSON Web Token (JWT). Required to be set as the password by eFTL, and FTL. For Pulsar it is used with token authentication.
- 
- **eftl_url:** The URL required for eFTL client connections. It is also reported in the status and Authentication Keys sections
- **ftl_url:** The URL required for FTL client connections. It is also reported in the status and Authentication Keys sections
- **ftl_application:** The name of the FTL application. Cannot be changed. Used by FTL only.
- **ftl_certificate:** The certificate to verify the authenticity of your FTL servers. Modified to fit on a single line. Used by FTL only.

> In case you are only interested in the *tcm_authentication_key*, you can also get it by clicking on the '**Copy To Clipboard**' icon, without downloading the configuration YAML file
{.is-info}


## TIBCO eFTL™ 6.6.0

**Useful Links:**
TIBCO eFTL™ 6.6.0 Documentation (Release 20/11/2021):
https://docs.tibco.com/pub/eftl/6.6.0/doc/html/

### Sample Project

This sample project contains the following two processes: 
- **Publisher.bwp:** This process demonstrates how to use the eFTL plug-in to publish messages over the Tibco Cloud Messaging service.


>![publisher.png](/publisher.png)
> *The process *Publisher.bwp**

- **Subscriber.bwp:** This process contains the eFTL Subscriber process starter activity. The eFTL Subscriber activity listens for an incoming message event and starts the job execution on receiving incoming records and writes them to a log.

>![subscriber.png](/subscriber.png)
> *The process *Subscriber.bwp**
