---
title: Cloud
description: Introduction to Cloud and Cloud Hosting
published: true
date: 2021-02-10T16:42:30.657Z
tags: 
editor: markdown
dateCreated: 2021-02-10T16:42:30.657Z
---

# Cloud

## Introduction

- Applications that rely on virtualized systems with easily scalable resources and on-demand access.
- **Virtualization**
	- **Why?** Optimises the resources of a server-farm → Server-Consolidation.
		- Decouples physical resources from the application.
		- One physical resource can be fractioned to exploit it better.
		- The same resource can be more easily shared.
		- Easier migration (also whilst running).
	- **Structure: **
		- The Virtualization Host Machine runs the Hypervisor Software either on a Host OS or on Bare Metal (directly on the HW).
		- The Virtual Web Server is the Virtual Machine that implements the Virtualization Service of the Hypervisor, virtualizing hardware resources, upon which it installs its own Guest OS.
- **Cloud characteristics:** Solving the scalability problem.
	- On demand and self-service resources.
	- Accessible via any connection to the web. Access is independent of location.
	- Elastic and scalable.
	- Easy to monitor and easy to implement a pay-per-use paradigm.
- **Deployment Models**
	- **Private Cloud:** Infrastructure for use of a single organization. Highly secure and personalized, but with limited scalability and higher costs. Can be on-premise, but also hosted, while still private.
	- **Community Cloud:** Infrastructure for use of a community of organizations with shared interests. 
	- **Public Cloud:** Infrastructure with a public scope and universal access (multitenancy). Cheaper and more scalable, but less secure.
	- **Hybrid Cloud:** Hybrid implementations of the above.
- **Cloud Based Integration:** → see iPaaS 
- **SOA:** Service Oriented Architecture: It’s a style of software design where services are provided to the other components by application components, through a communication protocol over a network.
	- Services + Virtualization ⇒ Cloud Computing

## Cloud Hosting
### IaaS, PaaS, SaaS, iPaaS

- As opposed to housing, hosting is the access to resources via the web, possibly managed by someone else.
- There are three layers in cloud computing for hosting: Infrastructure, Platform, Application:
	- **IaaS: Infrastructure as a Service:** Physical resources are made directly available to the user. The user controls the VMs.
	- **PaaS: Platform as a Service:** The user accesses the resources through a platform layer, which provides certain technologies (like a DBMS) through APIs. The user only controls their applications.
	- **SaaS: Software as a Service:** The user has access only to a finished application, over which they have very little control.
		- **iPaaS: Integration Platform as a Service:** It’s a suite of cloud services enabling development, execution and governance of integration flows connecting any combination of on premises and cloud-based processes, services, applications and data within individual or across multiple organizations. Provides Connectors for some applications (Salesforce...) via protocols (XML…). Moves and transforms data. Creates integration workflows.