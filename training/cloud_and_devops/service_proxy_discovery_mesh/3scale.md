---
title: 3Scale
description: 
published: true
date: 2021-03-23T16:10:47.229Z
tags: 
editor: markdown
dateCreated: 2021-03-23T16:04:28.894Z
---

# 3Scale
# 3 SCALE API MANAGEMENT PLATFORM

0. Prerequisites
1. Product Overview
2. Installation
3. Architecture
4. Accounts
5. Specific Components
6. Data Models
7. Web Portals

## 0. Prerequisites

### API
An __API__ is a _set of definitions and protocols for building and integrating application software_. API stands for application programming interface.

Benefits of API:
- __Agility__ - exposing data to external permits better combine of data, improved collaboration with partners
- __Innovation__ - expose data and services in a controlled way
- __Awareness__ - create new channels to the market
- __Revenue__ - generated directly or indirectly

### API ECONOMY
It is the place where supplier and consumer meet, and where trade access to digital assets via interfaces (API)
All digital initiatives are enabled or driven by API

__API ecosystem__ _encourages API providers and consumers to collaborate in order to deliver previously unimaginable customer experiences._

The main ecosystems use cases are the following:
- __Partner Ecosystems__ - Provides partners direct access to data and services to build via APIs
- __Costumer Ecosystems__ - Provides costumers direct access to data, billing and transaction capabilities via APIs

### OPENSHIFT CONTAINER PLATFORM
__Openshift__ is a platform that _provides cluster management capabilities and orchestrates containers, providing also the abstraction for packaging and creating Linux-based, lightweight container images_.
It runs on top of Kubernetes and Docker service.

## 1. Product Overview

3 Scale is a flexible and scalable _API management platform_ based on distributed architecture.
It __mediates between API consumers and API providers__.
It provides the capability to deploy separately the traffic layer and the management layer.
<br/>It is characterized by the following three main concepts:
- Visibility
- Control
- Flexibility and Scalability

It provides visibility and control of who can use assets and in which way.
It is capable to adapt to changes and scale with costumer needs.

The benefits of utilizing 3 Scale AMP are multiple:
- __Performance__ - It allows for Massive throughput of API calls and the costumer can deploy as many APIcast gateways as needed
- __Automation__ - 3 Scale exposes all APIs in the API Management Platform, so it is possible to automate the cycle of an API
- __Flexibility and Integration__ - Best of class in reliability/uptime (No single point of failure), Flexible deployment options (Software-as-a-Service (SaaS) or self-managed (on-premise/cloud)), API and infrastructure security, Extensibility of individual components (APIcast gateway, developer portal, billing, etc.) <br/>
![3scale-account-data-model.png](/3scale-account-data-model.png)

## 2. Installation
3 scale is offered as __Software-as-a-Service (SaaS)__ or __self-managed (on-premise/cloud)__.

_Openshift Container Platform is needed to deploy 3 scale On-premise._
The deploy is possible using one of the two official methods:
- Installation using the template
- Installation using the operator

It creates all the Openshift resources, including liveness and readiness probe support, all the needed persistent volumes and so on.
<br/>The installation time is about 4-5 minutes

Both of the above methods make it possible to __customize the installation__ in order to install the platform with or without the Apicast gateway deployed directly on Openshift.

The __best installation scenario__ is when the _Apicast/Apigateway, the 3 Scale Api Management Platform, and all the needed backend services are deployed on Openshift Container Platform_. <br/>
![all-ocp.png](/all-ocp.png)

## 3. Architecture

A high-level overview of the architecture is represented on the following schema.

The main components of the architecture are:
- API Gateway / API Cast
- API Manager (3 Scale AMP)
    - Admin Portal
    - Developer portal

![3SCALE ARCHITECTURE](./3Scale-Architecture-Detailed.png "3SCALE ARCHITECTURE")

### API Gateway / API Cast
The __API Gateway handles the API traffic and API policy execution__.
<br/>In more details it can handle access control, rate limiting, security filtering, logging, routing, caching.
It enforce traffic policy, access control and rate limits.
<br/>Usually it is based on the reverse proxy server _NGINX_.

It communicates with 3 Scale AMP in order to authenticate, authorize and report traffic of API requests.

Based on the implementation and configuration it can also operate in a asynchronous way with 3 Scale AMP, so the API requests continue to execute even if the 3 scale AMP is down.
<br/>y checking specific parameters against the history of previous API requests, it can authorize requests directly to the backend service, and then send a sync request to the 3 Scale AMP.

### API Manager
The __main operations__ done by the AMP are:
- Access control and security
- API contracts and rate limits
- Analytics and reporting
- Developer/Partner portal and docs
- Billing and payments

It is comprehensive of the full life cycle of the API:
- Define: Identify API services that deliver value to business layer
- Develop: Design, code, test, document, and standardize templates
- Publish: Run securely with policies and controls
- Manage and support: Offer community forums and documentation for collaboration
- Retire: End of life--unpublish, communicate, and remove from marketplace using version control best practice

## 4. Accounts
In 3 Scale AMP the accounts are divided into:
- Administrator
- Users
- Developer

### Administrator account
The admin user _has access to the account management features of the Admin Portal_
This user can create other users and accounts, and manage the provider accounts.

It can perform the following tasks:
- administration:
    - Adding/editing organization details (company name, timezone, logo)
    - Exporting data from Admin Portal
    - Managing administrator users
    - Integrating Red Hat Single Sign-On (SSO)
- Inviting users to admin portal
- Enabling administrator tasks to be carried by multiple users with different roles

### Users accounts
The users are usually the _members of the administration team_.

There are two types of users:
- admin - full access to all areas, and member management (such as inviting members)
- member - limited access to certain areas (such as analytics, developer portal) or services

It is possible to assign users specific rights, based on the following:
- By area (give access only to equivalent API)
    - Developer Portal (Account Management API)
    - Analytics
    - Billing
- By services (specify which services to get access to members)

### Developer accounts
The developer accounts are the _accounts subscribed to a particular API._
They represent the end users access to the APIS.

The developer account provides access to one or more services, and gives also access to the developer portal where users can manage their accounts.

Each developer account (that represents a developer group) can have multiple members some of whom can be the administrator of the developer account.

Two user roles:
- admin - can invite/add members, access all sections of Developer Portal
- member - can manage keys and subscriptions

## 5. Specific components
In the next paragraphs the main objects of the AMP will be briefly described.

### Methods
The methods can be _created for each HTTP method available on API endpoints_.
<br/>They allow tracking of API usage and are hit-based.
<br/>It is possible to define usage limits and pricing rules for each method, they are defined within each application plan

### Metrics
The metrics _tracks calls to an API_.
<br/>Hits is the built-in metric, it exists in each API service and is used to track the hits made to your API.
<br/>You can achieve finer granularity for the API usage tracking by defining Methods under the Hits metric.

### Mapping rules
They are used in order to _map API endpoints to the methods_.
<br/>To do so it is needed to choose an HTTP method on path and select the equivalent method to map against.
<br/>Different HTTP operations on one endpoint can be tracked separately (GET, PUT, POST, DELETE, etc.)

### Rate limits
The rate limits are used to _throttle the access to API resource by consumers_.
<br/>They are based on method, endpoint, or metric and are associated with a plan.
<br/>It is possible to configure different limits for different developer segments, through the use of application plans.
<br/>API authorization fails if the usage exceeds limit - but it is a soft rejection (the backend ultimately decide how to handle the rejection)

### Plans
The plans are used to _grant access to specific APIs and endpoints, limiting traffic and monetizing API usage._
<br/>There are four types of plans, that can be used alone or together:
- Application plans:
    - Let configure access rights to an API by specifying Rate Limits and Pricing Rules
    - All application must be associated with a plan
    - Can be customized for each application
- Account plans - establish prices and features at account level:
    - Configuration at account level, and for each account
    - Not limited to specific API service
    - Apply to all APIs accessed by account
- Service plans - establish prices and features on service level:
    - Configuration at service level
    - Not limited to specific application
    - Apply to all applications accessing service
- End-user plans - establish usage limits and pricing rules for endusers of an API:
    - Configuration at end-user level
    - Quotas can be applied to single user
    - Prevent rate limits from being consumed wholly by single user

### Application keys
The application key is a _type of credentials, for single application, in order to access APIs
It is associated with an application plan._
<br/>By default when an application is created, also the application key is created.

An API can use one of following for authentication, so the application key will be one of the following form:
- API key - It is a specific type of authentication pattern that combines the identity of the application and the secret usage token
- App ID and app key - It is a type of authentication that separates the identity and the secret token
- OAuth (OpenAuthentication) - It is a set of specifications that enable different authentication patterns with APIs

## 6. Data Models

### API/Admin Data Model
The following schema represents the Data Model for the API from the point of view of the API provider.

The following relations occurs:
- API PROVIDER creates 1 or N APIs
- ACCOUNT PLAN - is created for managing contract and creation of developers accounts; it is managed at application level and is usually left at single default and unchanged
- APPLICATION PLAN - define policies such as rate limits; each service can have multiple application plans
- APPLICATION - entity whose credentials are attached to each request
- APPLICATION KEY - is the credential to the application
- SERVICE PLAN - like application plan but is applied at service level to apply to all applications globally for the service
- USER PLAN - is optional and user plan that derives from application plan can apply limits to individual users

![3SCALE API DATA MODEL](./3Scale-API-Data-Model.png "3SCALE API DATA MODEL")

### Account Data Model
The following schema represents the Data Model for the user and the application entities from the point of view of the users/developers.

The following relations occurs:
- ACCOUNT SUBSCRIPTION - relates to API PROVIDER account (this is the account to login to 3scale and manage APIs)
- DEVELOPER ACCOUNTS - Accounts subscribed to a particular API, are the parents of the applications (when a new developer subscribe to API an application is automatically created that allows developers make calls to that API)
- USERS - objects that represents end users of application that belong to Developer Account, can be admin or users
- SERVICE SUBSCRIPTION - it's a contract or plan, between account and service, applications and applications plans are used to enforce contract for the service

![3SCALE ACCOUNT DATA MODEL](./3Scale-Account-Data-Model.png "3SCALE API ACCOUNT MODEL")

## 7. Web Portals

3 scale AMP exposes two type of portals, which are deployed separately and don't interfere with the access on the backend:
- Admin portal - for administration, API and Account management
- Branded developer portal - for exposing developer sign-ups, developer documentation


### Admin Portal
The admin portal is a __web console for API provider administrators to administrate API services such as API, accounts, services, application and documentation.__
<br/>It has a rich web interface for all management activities, it also provides _Admin REST API and the policies and configurations are synced with the API gateway_.

The main functionalities of 3 Scale admin portal are the following:
- API BizOps - Add/invite developers, approve accounts and applications, and contact developers
- Access control - Define API, create plans, set up rate limits and pricing rules
- Accounts - Manage administrator and member rights to use Admin Portal
- Analytics - Report API performance insights
- API DevOps - REST API for administrator, automating deployments
- API documentation - Document Swagger API using 3scale ActiveDocs
- Developer Portal CMS - Create and customize Developer Portal
- Billing - Integrate payment gateways and invoicing

#### API documentation
3 Scale offers the possibility to _make interactive documentation for API_.
<br/>Basing the __API specification on a JSON specification based on swagger 2.0__ you can have a functional documentation that helps explore, test and integrate.

When adding new service specification the following is needed:
- Name
- System name (reference the service specification from developer portal)
- Publish (visible or hidden)
- Description
- API JSON specification (secret ingredient of active docs)

The specification has to be generated based on swagger 2.0, 3 Scale doesn't help generate one.

### Developer Portal
The developer portal is a _portal for API consumers and developers_.
<br/>It is usually customized for each API provider to provide branded costumer experience.
It can __manage subscription, access API keys, create applications, access ActiveDocs, see API consumption, singups and reference materials for APIs (swagger, documentation, developer workflows).__

3 Scale provide a _content management system (CMS) to quickly create custom portals with HTML, CSS, JavaScript elements, liquid tags for processing and displaying data on portal and different authentication options._

#### Content Management System
It is possible to customize the CMS in order that all the portals match a branding.

Using CMS it is possible to customize feature visibility such that the following can be hidden:
- HTML fragments of controls are not rendered under portal
- Don't see create user button if multiple user features is hidden
- User plans 
- Multiple services
- Multiple applications
- Multiple users
- Webhooks
- Finance

One of the most important aspects of CMS is the fact that it _provides version control feature so it can be used to rollback to a previous version of the page/portal._

It makes possible to make a site accessible to all developers with URL (public site) or can be restricted to be accessible only by users with share access code (private site).

It offers also the _capability of restricting some parts of the developer portal to be accessible only by a specific group of developers._ In fact it possible to restrict whole pages and also only a specific block of context per page.


#### Liquid programming language
It is a simple __programming language for displaying and processing data.__
<br/>In 3 Scale it is used to expose server-side data to API developers.

Its main uses are:
- Alter Document Object Model (DOM) and page content based on server-side data
- Add logic to pages, layouts, and partials
- Manipulate email templates sent to developers

Liquid Markup
There are two types of liquid markup:
- logic tags -> conditional liquid statements including elements from other programming languages as conditional statements and loop statements
- output tags (also called liquid drop) -> display value of a tag between the curly braces

Other elements of liquid programming language are:
Filters -> enable filtering results from drops for converting values, group values on a key and so on
Context - Determines (describes) variables (drops) available to use on current page

#### Signup Workflows
Signup workflows are a critical aspect of developer experience.
It is a process that can be totally automatic or controlling.

It __allows sign-up of users from Developer Portal, in order to to allow API access for account plans, service plans, or application plans.__

For each plan above there are multiple options:
- Automated - No approvals required
- Approval - Admin to approve developer sign-up
- Plans - Allow plan changes directly by developers
- Default - Enable default plan for developers or if developer is required to do a next step and make a choice
- multiservice sign-ups - customize process to allow costumers to subscribe to different services

#### ActiveDocs
It is an _instantiation of swagger._
<br/>It is needed to build a swagger complaint specification of the API and add it to the admin portal, and the interactive documentation will be all set.

Developers can launch request to the API via the portal

It offers an interactive documentation served and rendered by Developer Portal, based on a swagger complaint specification of the API added to the admin portal.

It extends Swagger, to accommodate certain features needed for interactive documentation, such as:
- Autofill API keys
- Swagger proxy to call non-CORS-enabled APIs
- Test and call OAuth-enabled API
    - Client credentials flow
    - Resource owner flow