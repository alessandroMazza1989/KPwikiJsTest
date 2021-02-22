---
title: SOA
description: Service Oriented Architecture
published: true
date: 2021-02-22T10:17:45.524Z
tags: 
editor: markdown
dateCreated: 2021-02-22T10:17:45.524Z
---

# SOA

- **Goals**
1. Service Oriented Architecture paradigm concept 
2. Service design principles
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Standardized service contract
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Service loose coupling
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. service abstraction
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. service reusability
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. service autonomy
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. service statelessness
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. service discoverability
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. service composability
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. interoperability
3. Service orientation and the concept of applicazione soa
4. Service orientation e il concept of integrazione inside soa
5. Service models
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. service layers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. entity services
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. task services
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. utility services
6. Undertanding the difference between the  top down and the bottom up delivery strategies
- **External Llinks**
[SOA theory guide](http://serviceorientation.com/serviceorientation/index)
[SOA review blogspot](http://savedev.blogspot.it/2013/09/spaghetti-integration-to-soa.html)
[SOA tutorial](http://soaschools.com/)

--- 

## Introduction

While it can consist of a combination of different technologies, products, APIs, etc., an SOA implementation is intrinsically typified by the use of service-oriented solutions. An SOA separates functions into distinct units (services), which can be distributed over a network and can be combined and reused to create business applications. It is often seen as the evolution of distributed computing and modular programming. The technology of Web Services is the most likely connection technology of service-oriented architectures. However, while there is no one recognized definition of SOA, saying a solution uses web services is not enough for it to be immediately considered a service-oriented solution, as is often wrongly said. 
- **Core Values of SOA (Manifesto)** - Prioritize
	- Prioritize business value over technical strategy.
	- Prioritize strategic goals over project-specific benefits.
	- Prioritize intrinsic interoperability over custom integration.
	- Prioritize shared services over specific-purpose implementations.
	- Prioritize flexibility over optimization.
	- Prioritize evolutionary refinement over pursuit of initial perfection.
- **Why move from Traditional EAI to SOA?** 
	- The Limitations of Traditional EAI (Spaghetti Integration):
		- Monolithic, server-centric, centralized, hub-and-spoke.
		- Proprietary APIs, possible non-standard formats.
		- Integration limited by the MOM’s feature-set.
		- Intranet-focused. Hard to make visible from the outside.
		- Middleware set-up times are long (20+ months).
- **The Advantages of SOA:**
		- Separates functionalities of all Enterprise Information Systems and gathers them in a set of components that expose “portions of business logic” as services which are standard and documented.
		- More open, using standard technologies like XML, JSON, Web Services, Http/SOAP, REST, J2EE, etc.
		- Decouples service access from the communication protocols.

![soa_architecture.png](/soa_architecture.png)

- **ESB - Enterprise Service Bus:** SOA replaces the MOM with the ESB
	- What is it? https://cio-wiki.org/wiki/Enterprise_Service_Bus_(ESB) 
	- The ESB is tasked with exposing the available services, which are held in the Service Registry

![soa_esb_bpm_bam.png](/soa_esb_bpm_bam.png)

where **BPM** = Business Process Management and **BAM** = Business Activity Monitoring

- **The Service:** 
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/services 
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/the_service_orientation_design_paradigm

## Service Orientation

It’s the design paradigm of service-oriented solutions, with the service as the fundamental unit. Each service is assigned its own distinct functional context and consists of a set of capabilities related to this context. Those invokable capabilities are commonly expressed via a published service contract (much like a traditional API).

![soa_service_contract.jpg](/soa_service_contract.jpg)

- **The Need for Service-Orientation: **
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/the_need_for_service_orientation 
- **Service Compositions:**
	- https://patterns.arcitura.com/soa-patterns/basics/whatissoa/service_composition 
- **Service Inventory:**
	- https://patterns.arcitura.com/soa-patterns/basics/whatissoa/service_inventory 
- **Service Endpoint Interface (SEI):** It’s the application server’s component (class) which translates the application object to an XML format in order for it to be accessed as a service (as a SOAP message for example).

## Service Principles

- Standardized service contract
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/standardized_service_contract 
- Service loose coupling
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_loose_coupling 
- Service abstraction
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_abstraction 
- Service reusability
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_reusability 
- Service autonomy
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_autonomy 
	- Avoids circular dependencies when composing services
- Service statelessness
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_statelessness 
- Service discoverability
	- https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_discoverability 
- Service composability
	- https://patterns.arcitura.com/soa-patterns/basics/whatissoa/service_composition 
- Interoperabilità
	- https://patterns.arcitura.com/soa-patterns/basics/whatissoa/increased_intrinsic_interoperability

## SOA application concepts 

The SOA paradigm, with its multitude of reusable, agnostic services, allows requirements to be fulfilled not by building or extending applications, but by simply composing existing services into new composition configurations. **Therefore, applications become service-compositions.**

## Service orientation and SOA integration concepts 

https://patterns.arcitura.com/soa-patterns/basics/serviceorientation/service_orientation_and_the_concept_of_integration

## Service models

### Service layers

https://patterns.arcitura.com/soa-patterns/basics/soamethodology/service_layers
https://patterns.arcitura.com/soa-patterns/basics/whatissoa/service_models_and_service_layers

### Entity services

https://patterns.arcitura.com/soa-patterns/basics/soamethodology/entity_services

### Task services

https://patterns.arcitura.com/soa-patterns/basics/soamethodology/task_services

### Utility services

https://patterns.arcitura.com/soa-patterns/basics/soamethodology/utility_services

## Strategies approch: top-down and bottom-up

https://patterns.arcitura.com/soa-patterns/basics/soamethodology/top_down_vs_bottom_up
https://patterns.arcitura.com/soa-patterns/basics/soamethodology/choosing_a_delivery_strategy

## SOA Structure Pattern

There are three roles in each of the Service-Oriented Architecture building blocks: 
- service provider; 
- service broker, service registry, service repository; 
- service requester/consumer.

The service provider works in conjunction with the service registry, debating the whys and hows of the services being offered, such as security, availability, what to charge, and more. This role also determines the service category and if there need to be any trading agreements.
The service broker makes information regarding the service available to those requesting it. The scope of the broker is determined by whoever implements it.
The service requester locates entries in the broker registry and then binds them to the service provider. They may or may not be able to access multiple services; that depends on the capability of the service requester.

## SOA Implementation

Typically, Service-Oriented Architecture is implemented with web services, which makes the “functional building blocks accessible over standard internet protocols.”

## SOA and Cloud Computing

- In a nutshell, using cloud computing allows users to easily and immediately implement services tailored to the requirements of their clients, “without needing to consult an IT department”.
- Of course, when using cloud computing, users are often at the mercy of the provider vis-à-vis reliability and security.
- https://www.oracle.com/technical-resources/articles/middleware/soa-ind-soa-cloud.html