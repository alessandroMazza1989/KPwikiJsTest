---
title: JMS
description: Java Message Service
published: true
date: 2021-02-22T10:02:19.822Z
tags: 
editor: markdown
dateCreated: 2021-02-22T10:02:19.822Z
---

# JMS

- **Goals**
1. What is a Messaging system?
2. JMS API and related Concepts
3. JMS API Programming Model
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Connection Factories
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Destinations
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Connections
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Sessions
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Message Producers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Message Consumers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Message Listeners
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Message Selectors
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Messages
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> j. Message Headers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> k. Message Properties
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> l. Message Bodies
- **External Links**
[JMS Guide (relevat topics up to chapter 3 included)](http://docs.oracle.com/javaee/1.3/jms/tutorial/1_3_1-fcs/doc/jms_tutorialTOC.html)
- **Tools & Lab**
Lab: Installation of a EMS server on the previously created Centos 6.5 VM.
Lab: Creation of a centos VM using vagrant. [Link to vagrant guide](https://docs.google.com/document/d/1kypDQ33wxUAE1-_Cm94UNwGtmWy0_UGw5SePVHutzws/edit?usp=sharing )
Lab [KP linux exercises](https://drive.google.com/open?id=0BydghG4Au4HfUzFobUxTU0wtV1E)

---

## Basic JMS API Concepts

### The JMS API

- The Java Message Service is a Java API that allows applications to create, send, receive, and read messages. It provides loosely coupled, asynchronous, reliable communication.
- The JMS API is now an integral part of of the J2EE platform, and provides the following features:
	- Application clients, Enterprise JavaBeans, and Web components can send/receive sync. JMS messages
	- Application clients can also async. receive JMS messages.
	- Message-driven beans, which enable async. message consumption.
	- Message sends and receives can participate in distributed transactions.

### The JMS API Architecture

- **Components**
	- **JMS provider:** is a messaging system that implements the JMS interfaces and provides administrative and control features.
	- **JMS clients:** are the programs or components, written in Java, that produce and consume messages.
	- **Messages:** are the objects that communicate information between JMS clients.
	- **Administered Objects:** are preconfigured JMS objects created by an administrator for the use of clients. The 
		- **Destination objects:** → see administered objects
		- **Connection factories:** → see administered objects
	- **Native Clients:** are programs that use a messaging product's native client API instead of the JMS API.
  
![jms_architecture.gif](/jms_architecture.gif)

### Messaging Domains

There’s a different domain for each approach (PTP or pub-sub) and there is support for both concurrently.
- **Point-to-Point Messaging (PTP) Domain** → Useful when there’s only one consumer for that message.
	- Each message is addressed to a specific queue, which retains the message until consumed or expired.
	- Each message has only one consumer.
	- A sender and a receiver of a message have no timing dependencies. The receiver can fetch the message whether or not it was running when the client sent the message.
	- The receiver acknowledges the successful processing of a message.

![jms_queue.gif](/jms_queue.gif)

- **Publish/Subscribe Messaging Domain** → Useful when there are multiple consumers for that message.
	- Clients address messages to a topic. 
	- Publishers and subscribers are generally anonymous and may publish or subscribe to the content hierarchy.
	- The system takes care of orchestrating proper distribution.
	- Topics retain messages only as long as it takes to distribute them to current subscribers.
	- Publishers and subscribers have a timing dependency. A client that subscribes to a topic can consume only messages published after the client has created a subscription, and the subscriber must continue to be active in order for it to consume messages.
		- **Durable Subscriptions:** allow clients to receive messages sent while the subscribers are not active.
    
![jms_topic.gif](/jms_topic.gif)

### Message Consumption

Messaging products are inherently asynchronous, but the JMS Specification uses this term in a more precise sense.
- **Synchronous Consumption:** A subscriber or a receiver explicitly fetches the message from the destination by calling the receive method. The receive method can block until a message arrives or can time out if a message does not arrive within a specified time limit.
- **Asynchronous Consumption:** A client can register a message listener with a consumer. A message listener is similar to an event listener. Whenever a message arrives at the destination, the JMS provider delivers the message by calling the listener's onMessage method, which acts on the contents of the message.

## The JMS API Programming Model

**Building blocks:**
1. Administered Objects
	1. Connection Factories
	2. Destinations
2. Sessions
3. Message Producers
4. Message Consumers
5. Messages

![jms_api.gif](/jms_api.gif)

### Administered Objects

- Ordinarily, an administrator configures administered objects in a **Java Naming and Directory Interface (JNDI)** API namespace, and JMS clients then look them up, using the **JNDI API**. ⚠️They are passed as Strings!
	- What’s a JNDI Server? See JNDI.
- To perform administrative tasks, like maintaining the Administered Objects, you can use the tool: j2eeadmin.
	- Type j2eeadmin with no arguments for help.
- **Administered Objects**
	- **CONNECTION FACTORIES:** object a client uses to create a connection with a provider.
		- Each connection factory is an instance of either of the following interfaces:
			- **QueueConnectionFactory**
			- **TopicConnectionFactory**
		- 2 connection factory objects come preconfigured with the J2EE SDK.
		- To create new ones use:
			- j2eeadmin -addJmsFactory jndi_name queue
			- j2eeadmin -addJmsFactory jndi_name topic
	- **DESTINATIONS**
- **CONNECTIONS**
- **SESSIONS**
- **MESSAGE PRODUCERS**
- **MESSAGE CONSUMERS**
	- **Message Listeners**
	- **Message Selectors**
- **MESSAGES**
	- **Headers**
	- **Properties**
	- **Bodies**
- **Exception Handling**
- ⚠️ An application only needs one connection to a messaging system, but each component in the application that wishes to be able to send and receive messages independently needs its own session.
- TODO: Draw a graph with all the functions

## JNDI

### Example
See here: https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReplyJmsExample.html