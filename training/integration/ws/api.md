---
title: API
description: Application Programming Interface
published: true
date: 2021-02-22T12:30:09.786Z
tags: 
editor: markdown
dateCreated: 2021-02-22T12:30:09.786Z
---

# API

- **Goals**
1. Difference between API and Web Services
2. Inner workings of web services
3. Why use web services?
- **External Links**
[Difference between API and web services explained 0](https://www.linkedin.com/pulse/difference-between-api-web-service-chitrakannan-balasubramanian/)
[Difference between API and web services explained 1](https://testautomationresources.com/api-testing/differences-web-services-api/)

---

## Introduction

- **Definition**
	- A computing interface that defines interactions between multiple software intermediaries. (Calls or requests that can be made, the data formats that should be used, the conventions to follow, etc.)
- **Characteristics**
	- Not necessarily consistent with standard protocol specifications.
	- Rarely offered openly on the web, but instead only reachable through ad hoc software libraries.
	- In fact, it doesn’t have to be accessible via the web.
	- They usually give access to internal and atomic functionalities of a single application or system.
	- They are basically the interfaces of libraries of code.

## Web-Services (WS)

- **Definition**
	- A service or functionality offered via the web to clients via a URI built with very standard protocols like HTTP, SOAP, WSDL, REST, languages like JMS, and markup like XML, XSD, JSON.
- **Characteristics**
	- Publishable and reachable on the web via a URI using open protocols.
		- This would make anything online sound like a web service, like accessing a website. However, the difference between accessing a website and using a webservice is that the first one is tailored for human consumption, while the second for application consumption.
	- Self-contained and self-describing.
	- Their interface is well-documented with highly standardized specifications.
	- They often realize more articulated, non-atomic business processes, sometimes by calling other WS. 
		- (This leads to Service Orchestration and consequently to an SOA.)
	- In general, they use XML to code data and SOAP to transport it.
  
## Web-Services vs API

- Web services are basically standardised APIs accessible exclusively via the web.	
- All web services are APIs, but not all APIs are Web-Services.
- Web services are more articulated, whereas APIs should be atomic (convention that is rarely respected).
- Web services are generally less performant, as they require quite a bit of overhead information (e.g., the XML tags) and a layer of further encapsulation and encoding for them to be universally consumed.