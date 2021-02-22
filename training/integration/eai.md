---
title: EAI
description: Enterprise Application Integration
published: true
date: 2021-02-22T09:44:06.123Z
tags: 
editor: markdown
dateCreated: 2021-02-22T09:08:06.252Z
---

# EAI

- **Goals**
1. General concepts pertaining system integration
2. Integration Styles
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. File Transfer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Shared Database
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Remote Procedure Invocation
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Messaging 
3. Messaging Systems
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Message Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Pipes and Filters
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Message Router
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Message Translator
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Message Endpoint
4. Messaging Channels
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Point-to-Point Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Publish-Subscribe Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Datatype Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Invalid Message Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Dead Letter Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Guaranteed Delivery
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Channel Adapter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Messaging Bridge
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Message Bus
5. Message Construction
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Command Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Document Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Event Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Request-Reply
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Return Address
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Correlation Identifier
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Message Sequence
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Message Expiration
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Format Indicator
6. Message Routing
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Content-Based Router
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Message Filter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Dynamic Router
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Recipient List
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Splitter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Aggregator
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Resequencer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Composed Msg. Processor
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Scatter-Gather
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> j. Routing Slip
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> k. Process Manager
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> l. Message Broker
7. Message Transformation
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Envelope Wrapper
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Content Enricher
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Content Filter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Claim Check
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Normalizer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Canonical Data Model
8. Message Endpoints
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Messaging Gateway
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Messaging Mapper
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Transactional Client
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Polling Consumer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Event-Driven Consumer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Competing Consumers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b  Message Dispatcher
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Selective Consumer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Durable Subscriber
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Idempotent Receiver
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Service Activator
- **External Links**
[Integration theory guide](http://www.enterpriseintegrationpatterns.com/Introduction.html)

---

## Introduction

- Systems rarely live in isolation. They need to interoperate, often on a global scale. This presents some challenges:
	- **Networks are unreliable:** distributed computing has to be prepared to deal with a large set of reliability issues.
	- **Networks are slow:** performance must be taken into account.
	- **Applications are different:** they have different languages and interfaces.
	- **Change is Inevitable:** an integration solution must keep pace with changes, minimizing dependencies between systems and using loose coupling between applications.
- **Integrated Systems vs Distributed Systems**
	- Distributed applications are, as the term suggests, distributed on n-tiered architectures. Every tier (client, server, other) is highly coupled with the ones before and after it, and synchronicity and response times are extremely important, especially for the client.
	- Integrated applications, instead, must be decoupled, asynchronous, and must be able to act independently from one another. They also shouldn’t require immediate responses to keep functioning.
  
## Integration Styles

- Solutions to the aforementioned challenges: (Sometimes more than one can be used at the same time.)
	- **File Transfer:** Communication via a file with a certain format (XML), on a certain location at a certain time.
		- File transformation (translation) may be necessary, and is performed by the integrators.
	- **Shared Database:** Applications share a DB, with a certain shared schema.
	- **Remote Procedure Invocation (RMI):** Applications expose remote functionalities, which are synchronous.
	- **Messaging:** Applications publish messages on a common message channel. Each application can read the messages asynchronously, but the message format must be agreed upon. 

## Messaging and its Patterns

### What, How, Why and Why not

- **What**
	- A message is some data structure: string, byte array, or object.
	- A message has a header and body.
		- **Header:** meta-information.
		- **Body:** content of the message.
- **How**
	- A message is sent via channels from sender to receiver.
	- A Messaging System or Message-Oriented Middleware (MOM), configures the channels and coordinates the reliable transmission of messages, accounting for the unreliability of the network.
	- **5 steps of message transmission:** Create → Send → Deliver → Receive → Process
		- Note that sending and receiving occur on the local machines, where the message gets encapsulated and opened respectively, whereas it’s the channel that takes care of delivering the message.
	- **Transmission Methods**
		- **Send and Forget:** After sending the message the local machine can do other things, as it’s now the channel’s responsibility to ensure the message is delivered.
		- **Store and Forward:** The messaging system actually stores the message on the sender’s machine, before sending it, then does the same on the receiver, creating a buffer of messages on both sides.
- **Why**
	- Messaging is good for frequent, fast, reliable, asynchronous data transfer.
	- **Why it’s better than other integration styles**
		- It’s more immediate than File Transfer.
		- It’s better encapsulated than Shared Database.
		- It’s more reliable than Remote Procedure Invocation.
	- **Other benefits:**
		- **Remote Communication:** necessary when sharing machine memory is not an option.
		- **Platform/Language Integration:** it can translate formats for different platforms (Message Bus).
		- **Asynchronous Communication:** this ensures there are no hold-ups during communication.
		- **Variable Timing:** sender/receiver are decoupled so that they can’t affect each other’s performance.
		- **Throttling:** receivers can throttle incoming message flow on the channel, so they don’t overload.
		- **Reliable Communication:** store-and-forward methods guarantee redundancy and reliable delivery.
		- **Disconnected Operation:** allows for synchronization once a connection is available.
		- **Mediation:** the system acts as a hub for many different applications, balancing loads accordingly.
		- **Thread Management:** no application needs a thread to stop and wait for a reply or ack for each message. Only a few listener threads are necessary, so most others remain available.
- **Why Not: Challenges of Asynchronous Messaging**
	- **Complex:** event-driven programming with event handlers is more complicated.
	- **Sequence issues:** message delivery is guaranteed, but not the time of delivery or its sequentiality.
	- **Synchronous scenarios:** some scenarios might require the re-introduction of synchronicity.
	- **Performance:** messaging systems add a lot of overhead to the communication transaction.
	- **Limited Platform Support:** many proprietary messaging systems are not available on all platforms.
	- **Vendor Lock-in:** many proprietary messaging systems rely on proprietary protocols.
		- **New issue:** integrating multiple integration solutions!
    
### Commercial Messaging System Types

- **Operating Systems:** some OSs and DBs integrate messaging features within them (MSMQ, Oracle AQ).
- **Application Servers:** JMS is incorporated on virtually all J2EE application servers.
- **EAI Suites:** proprietary, feature-rich suites like TIBCO, IBM WebSphere MQ… (Most include JMS support.)
- **Web Services Toolkits:** web-service based solutions.

### Commercial Messaging System Terminology (JMS and TIBCO)

- **Terminology Map for JMS and TIBCO**

| Enterprise Integration Patterns 	|            JMS            	|         TIBCO        	|
|:-------------------------------:	|:-------------------------:	|:--------------------:	|
| Message Channel                 	| Destination               	| Topic                	|
| Point-to-Point Channel          	| Queue                     	| Distributed Queue    	|
| Publish-Subscribe Channel       	| Topic                     	| Subject              	|
| Message                         	| Message                   	| Message              	|
| Message Endpoint                	| Message Producer/Consumer 	| Publisher/Subscriber 	|

### Messaging Components

- **Message Channel:** also known as queues, are logical pathways that connect the programs and convey messages. One application writes information on a particular channel, and another application reads it from that channel. There can be many channels for different types of messages.
- **Message:** it encapsulates the data that needs to be transmitted.
- **Pipes and Filters:** architecture that splits complex tasks into many independent steps (filters) which are then piped.
- **Message Router:** transparent component which routes messages to the correct message channel. It’s itself a filter, but with multiple output channels.
- **Message Translator:** transforms messages to overcome format-barriers between incompatible systems (legacy).
- **Message Endpoint:** interface which an application uses to connect to channels and encapsulate data into messages.

### Messaging Channels

- **Fixed Set of Channels:** In general, channels cannot be created dynamically at runtime. They must be agreed upon at design-time. (There are exceptions.) Determining which set of channels an application needs is a non-banal, iterative process. When new functionalities are needed the set of channels might need to be extended.
- **Channel Direction:** while they don’t really have a direction (they act more like a common bus) channels can be thought as unidirectional, so, in general, when two applications communicate they ought to use two channels.
- **Channel Types**
	- **Point-to-Point Channel:** ensures that only one receiver will receive a particular message, even if there are many receivers listening on the same channel.
	- **Publish-Subscribe Channel:** broadcasts a copy of a particular event to each receiver on the same channel.
  
![messaging_publish-subscriber.png](/messaging_publish-subscriber.png)

- **Datatype Channel:** channels which ensures that messages will all be of the same type and format.
- **Invalid Message Channel:** a special channel for messages that could not be processed by their receivers.
- **Dead Letter Channel:** a special channel for messages that cannot or ought not be delivered.
	- **Amazon SQS example:** When a consumer fetches a message from a queue, it remains on the queue, but it is also made invisible to keep other consumers from fetching it. The consumer is then responsible for deleting it from the queue. If they don’t for some reason, the message becomes visible again after the Visibility Timeout expires. When this happens, the message's receive count is increased. When this count reaches a configured limit, the message is placed in a designated Dead Letter Queue.
- **Guaranteed Delivery:** makes messages persistent so that they are not lost even if the messaging system crashes.
	- All machines store outgoing messages locally, and they are not deleted until a copy is successfully delivered.
- **Channel Adapter:** it’s the interface between application (via its APIs) and the message channel. It’s also necessary when one wants to connect an application to a channel as “read-only” (i.e., without the ability to send messages), hence without having to install a whole messaging client on the machine.
- **Messaging Bridge:** connects multiple messaging systems (their channels), replicating the messages between them.
	- It’s basically a set of channel adapters, which can also transform messages for different systems.
- **Message Bus:** a middleware component connecting different separate applications (i.e., the flow of their messages) via a shared set of interfaces.

### Message Construction

- **Message Intent:** a sender can have different intentions for what it expects the receiver to do with its messages:
	- **Command Message:** it’s the equivalent of a remote procedure call. Invokes a procedure on an application.
		- (A SOAP request is a command message.)
	- **Document Message:** transmits one of the sender’s data structures to the receiver.
	- **Event Message:** transmits a notification.
- **Request-Reply:** scenario in which, after sending a message, the receiver expects an acknowledgement (event message) or maybe an actual result (document message), to be sent to a return address with an identifier:
	- **Return Address:** channel on which the response is expected.
	- **Correlation Identifier:** identifies what request the current message is a response to.
- **Message Sequence:** solution to sending large amounts of data, which is split into a sequence of messages.
- **Message Expiration:** for time-sensitive messages. Expired messages (both outgoing or incoming) are discarded.
- **Format Indicator:** enables the sender to tell the receiver the format of the message.

### Message Routing

- **Simple Routers:** route messages from one inbound channel to one or more outbound channels.
	- **Dynamic Router:** allows the routing logic to be modified by sending control messages to a certain control port.
	- **Patterns** (Each can be both Normal or Dynamic)
  
|        Pattern       	| N° of msgs consumed 	| N° of msgs published 	|  Stateful?  	|                                                                                                                       Details                                                                                                                       	|
|:--------------------:	|:-------------------:	|:--------------------:	|:-----------:	|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| Content-Based Router 	|          1          	|           1          	| No (mostly) 	| Bases routing on message content inspection.                                                                                                                                                                                                        	|
| Message Filter       	|          1          	|        0 or 1        	| No (mostly) 	| A content-based router that also filters messages based on the inspection and some criteria. Useful to recipients on a Publish-Subscribe channel, especially when messages are not specifically routed, and lots of messages travel on the channel. 	|
| Recipient List       	|          1          	|     0 or multiple    	|      No     	| Inspects a message and forwards it to none or more channels associated with the recipients.                                                                                                                                                         	|
| Splitter             	|          1          	|       multiple       	|      No     	| Splits messages that contain large elements into smaller messages, then processed individually.                                                                                                                                                     	|
| Aggregator           	|       multiple      	|           1          	|     Yes     	| Recombines split messages into a single message.                                                                                                                                                                                                    	|
| Resequencer          	|       multiple      	|       multiple       	|     Yes     	| Puts out-of-sequence messages back in sequence, especially when multiple computers with different speeds need to process the same batch of messages, storing them until all computers have processed them.                                          	|

- **Composite Routers:** thanks to filter separation, multiple simple routers can be combined to create more complex message flows.
	- **Parallel:** Routers routing a single message to many clients, and reassemble the replies into a single message.
		- **Composite Msg. Processor:** splits the message, routes the sub-messages to their destinations and re-aggregates the responses back into a single message. (Splitter → Router → Aggregator)
		- **Scatter-Gather:** broadcasts the same message (no split) to multiple recipients and re-aggregates the responses back into a single message.
	- **Sequential:** Routers that route messages through a sequence of individual steps.
		- **Routing Slip:** attaches a special component (a “routing slip”) to the message which defines the different stops the message must make on its path.
		- **Process Manager:** more flexible version of a routing slip system, but the message needs to return to a central component each time to be rerouted to the next stop on its path.
- **Architectural Patterns:** describe architectural styles based on Message Routers.
	- **Message Broker:** it’s the hub in the hub-and-spoke architectural style.
- **SUMMARY: Which Simple Router for Which Purpose**

![messaging_routing.gif](/messaging_routing.gif)

### Message Transformation

Variants of the Message Translator Pattern:
- **Envelope Wrapper:** solves message format conflicts by wrapping data inside an envelope that is compliant with the messaging infrastructure.
- **Content Enricher:** special transformer that accesses an external data source (DB?) in order to augment a message with missing information.
- **Content Filter:** removes unimportant data items from a message leaving only important items, simplifying it.
- **Claim Check:** stores the message in a persistent store (on some third party machine) and passes a Claim Check to subsequent components. These components can use the Claim Check to retrieve the stored information. Useful when passing large amounts of data which is not required immediately.
- **Normalizer:** forwards messages with different formats do the relative Message Translators in order to output only messages with a common format.
- **Canonical Data Model:** it presumes the existence of a common model (format) for all transferred messages. All applications will then need a translator before them, but one that only translates to (and from) that particular format.

### Message Endpoint Patterns 

Endpoints are how applications connect to a messaging system (through its APIs, such as JMS).
- Sender and Receiver Patterns (shared by sender and receiver)
	- **Messaging Gateway:** it encapsulates message specific code. It’s a class that wraps messaging-specific method calls and exposes domain-specific methods to the application, hiding the messaging system from it.
	- **Messaging Mapper:** transparently converts the data between the application and the messaging infrastructure, usually from objects to messages and vice-versa. 
	- **Transactional Client (Producer/Consumer):** makes the client transactional, so that they can directly control the transactions with the messaging system.
- **Receiver Patterns:** receiving is harder than sending messages (request volume problem).
	- **Polling Consumer:** best approach for throttling because if the server is busy, it won’t run the code to receive more messages, so the messages will queue up. (Server decides when to consume.)
	- **Event-Driven Consumer:** processes messages as fast as they arrive, which could overload the server; but limiting the number of consumers effectively throttles the consumption rate. (Server consumes on arrival.)
	- **Competing Consumers:** pattern that places more consumers on a single channel working concurrently.
		- ⚠️This only works with point-to-point channels; on publish-subscribe messages just get copied.
	- **Message Dispatcher:** it’s a single consumer that receives a message but delegates it to a performer for processing. It can also implement throttling behavior.
	- **Selective Consumer:** it’s basically a filter that only allows consumption of messages on the channel that match certain criteria.	
	- **Durable Subscriber:** solves the publish-subscribe problem where a consumer who is currently offline needs certain data on a channel. Normally he’d miss the message, but a durable subscriber can store the message on their behalf, and deliver it to them when they are back online.
	- **Idempotent Receiver:** solves the problem of (unexpected) repeated messages on the channel. An idempotent receiver can receive the same message multiple times without consequences for the application.
- **Service Activator:** sometimes a service needs to be invoked synchronously, sometimes asynchronously. Through a service activator (housed on the receiver’s side) one may chose how to access the service, whether directly and synchronously via a procedure call, or asynchronously via a message.