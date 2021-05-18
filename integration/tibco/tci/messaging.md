---
title: Messaging
description: eFTL
published: true
date: 2021-05-18T14:38:50.541Z
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

TIBCO ActiveMatrix BusinessWorks™ Plug-in for TIBCO eFTL™ User's Guide
https://docs.tibco.com/pub/bwplugineftl/6.0.0/doc/html/
### Tutorial - Sample Project 

This sample project shows how to use the plug-in to send and receive messages using TIBCO ActiveMatrix BusinessWorks™ Plug-in for TIBCO eFTL™.

**PROCESSES:**

The project contains the following two processes: 
- **Publisher.bwp:** This process demonstrates how to use the eFTL plug-in to publish messages over the Tibco Cloud Messaging service.

>![guid-cb0a39fd-a427-4b4d-8c78-c5fd98b9ff05-display.png](/guid-cb0a39fd-a427-4b4d-8c78-c5fd98b9ff05-display.png)
>*This figure describes the design process for eFTL Publisher*

It is composed of a starter activity (*Timer*) and an *eFTLPublisher* activity, which is an asynchronous activity belonging to the eFTL library palette that takes input from the shared resource and publishes or sends messages to the TIBCO Cloud Messaging service.

>![publisher.png](/publisher.png)
> *The process *Publisher.bwp**

In the general tab it is required to indicate an eFTL Connection, i.e. create and configure an eFTL Connection Resource (or eventually, if it has already been created, choose it) 

>![inkedtcmeftlgeneral_li.jpg](/inkedtcmeftlgeneral_li.jpg)

>![tcmeftlcreateresource.png](/tcmeftlcreateresource.png)

> The eFTL Connector shared resource describes the connection parameters for establishing TIBCO Cloud Messaging connection, and so you must have an active TCM subscription before you create a connection. 
{.is-info}

To properly configure the eFTL Connection Resource, provide the **Connection URL** and the **Authentication Key** obtained from the YAML file *tcm-config.yaml* (see Authentication Key Section for more details). Then proceed to test the connection. If everything went well, the message "Connection successful" will appear.

>![tcmeftlconnector.png](/tcmeftlconnector.png)

> The authentication key is managed as a password field. Although you can assign its value to a module property, it is not possible to promote this property at the application level and then import the project to TIBCO Cloud Integration, nor is it possible to deploy it due to security reasons ("*BW App import error: Error while using privacy service*")  
{.is-warning}


Through the Input Editor tab you can specify any data structure for the message to be published. Lastly, the Input tab has the following mandatory fields: **Destination**, that is the destination for a message to be sent, and **Message**, which is the data element defined in the Input Editor tab    


>![inkedtcmeftlinput_li.jpg](/inkedtcmeftlinput_li.jpg)



- **Subscriber.bwp:** This process contains the eFTL Subscriber process starter activity. The eFTL Subscriber activity listens for an incoming message event and starts the job execution on receiving incoming records and writes them to a log.

>![guid-fb02dd72-976c-4f24-8598-719c01c6fc2c-display.png](/guid-fb02dd72-976c-4f24-8598-719c01c6fc2c-display.png)
>*This diagram describes the design process for eFTL Subscriber*

>![subscriber.png](/subscriber.png)
> *The process *Subscriber.bwp**

As for the *eFTLPublisher* activity, you are asked to specify the eftl connecton resource in order to communicate with a TIBCO Cloud Messaging service. In the General Tab it is also  possible to change the type of subscriber, setting it as *Durable* (default *False*). In this way incoming messages are preserved if the subscriber application fails, and delivered after the subscriber is back online. Note that if you choose this option *Durable Name* and *Durable Type* fields are displayed and must be valorized.

> Currently, only Shared durable subscriber type is supported.
{.is-info}

Unlike the eFTLPublisher, the destination to which the subscriber is listening must be provided in the General tab. If the *Destination* field is not blank, the eFTLSubscriber will receive only messages with the specific destination set. Otherwise,if left blank, the subscriber receives all messages.

The possibility of using a *Content Matcher* is also given, which, due to the presence of the destination, is less relevant and fundamental than in the case of an FTL subscriber. Nevertheless, it can be useful to perform specialized filtering on messages associated with a specific destination. Specifically, this *Content Matcher* specify the eFTLSubscriber activity's interest in a message by selecting a subset of messages from a message stream according to the fields and values in those messages.

> The data types supported as part of content matcher are string, long, or boolean.
{.is-info}

Finally,two different acknowledge subscriber messages modes are supported: 
- **Auto:** eFTL library automatically acknowledges the message when the application callback returns.
- **Explicit:** Must be used with a Confirm activity in the ActiveMatrix BusinessWorks™ process to explicitly acknowledge the message.

>![tcmeftlsubgeneral.png](/tcmeftlsubgeneral.png)

The Output Editor tab defines the schema to use for incoming messages. The Output is a data element defined according to the XML schema defined in the Output Editor tab.
>![tcmeftlsuboutput.png](/tcmeftlsuboutput.png)

### Info Notes

> It has been verified that it is possible, once deployed on TIBCO Cloud Integration one or more applications with publishing functions, to correctly receive the messages on any other child organization (if of course the eFTL Connector is correctly configured and the connection is successfully tested).
{.is-info}


---

