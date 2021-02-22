---
title: REST
description: REpresentational State Transfer
published: true
date: 2021-02-22T13:27:28.219Z
tags: 
editor: markdown
dateCreated: 2021-02-22T13:26:29.839Z
---

# REST

- **Goals and External Links**
1. [What is REST](https://www.codecademy.com/articles/what-is-rest)
2. [Guide](https://restfulapi.net/resource-naming/)

- **Tools & Lab**
[Tool: Download Postman](https://www.getpostman.com/downloads/)
[Tool: Download Swagger]( https://swagger.io/tools/swagger-editor/download/)
[Lab: Try Any API](https://any-api.com/)

---

## Definition

- It’s a **style of software architecture**. So it’s not a standard, a protocol, or an architecture, but a series of guidelines.
- It supports HTTP only. In fact it’s based on the sole use of HTTP, without adding overhead to it.
- It can use many data formats, including HTML, XML, and JSON (mostly the last two).
- **Why Representational State Transfer?** Because what REST does is transfer the state of an application object over the web by sending only a representation of its state, and not the object itself, which is application-dependent.
- **Ingredients for a RESTful Client**
	- An **HTTP client**. (For simple purposes, and as a rudimental debugger, any browser will do.)
	- The **URIs** of the resources that interest the client.
	- The ability to interpret the **format** representing the resources.
  
## RESTful Architecture Principles

- **Principles**
	- Resource identification (URI)
	- Explicit use of HTTP methods.
	- Self-describing resources. 
	- Links between resources.
	- Stateless communication.

### Resource identification (URI)

- Resource identification is carried out via classic use of URIs.
- **URI Syntax:** http://my.server/page?par1=val1&par2=val2
	- The ‘?’ indicates **query parameters** with the syntax: name=value
	- **Multiple parameters** can be concatenated with ‘&’.
	- **Whitespaces** can only be expressed with ‘%20’ or’+’.
- **URI Styles:** They are interchangeable, but it’s best to stick to one style for the whole web service if possible.
	- **Style 1:** http://my.server/order/5     	← path param 	→ USE THIS WHENEVER POSSIBLE
	- **Style 2:** http://my.server/order/?id=5 	← query param 	→ USE FOR WHERE-LIKE STATEMENTS
- **Recommendations for URI Syntax**
	- URIs should strive to be human-readable, or at least have a consistent logic behind them. For example:
		- http://www.myapp.com/rest/products?color=red
		- http://www.myapp.com/rest/products/7654
	- **Prefer the use of nouns to verbs:** That’s because with REST we access resources, not functions or actions. 
	- **Keep the URIs as short as possible** without compromising readability.
	- **Prefer a Positional Notation:** In other words position the URI elements in a hierarchical order when possible. 
	- **Avoid Extensions:** That’s because they constrain a web service with its current implementation.
  
**Note:** *There are also Header Parameters that can be set to make a REST query, but they should be reserved for special cases, as custom headers make it impossible to reach the service via the simple URI.*

### Explicit use of HTTP methods

- REST simply makes use of the 4 basic HTML actions to CRUD resources.
- **CRUD to HTTP Mapping**

| CRUD Operation 	| HTTP Method 	|                       Description                       	|
|:--------------:	|:-----------:	|:-------------------------------------------------------:	|
|     Create     	|     POST    	|  Creates a new resource.                                	|
|      Read      	|     GET     	|  Retrieves a resource.                                  	|
|     Update     	|     PUT     	|  Updates a resource or modifies its state. (IDEMPOTENT) 	|
|     Delete     	|    DELETE   	|  Deletes a resource                                     	|

- Example of a Read Request

> GET /clients/1234						→ The requested resource.
HTTP/1.1							→ Protocol version.
Host: www.myapp.com					→ The URI of the resource.
Accept: application/vnd.myapp.client+xml		→ The format accepted. (OPTIONAL)

- It is then up to the client’s application to eventually deserialize and interpret the response in that format.

⚠️**Note:** *In the context of REST it is forbidden to use HTTP methods arbitrarily, like using GET to send information.*

### Self-describing resources

- The Web Service, as we said, only sends a representation of the resource, which can be in formatted arbitrarily. However, it is standard-practice to use a **MIME type**.
- **MIME Type: Multipurpose Internet Mail Extension:** is the standard representation of formats for the web.
	- **MIME Syntax:** type/subtype
		- **type:** refers to a logical grouping of closely related MIME types; it’s a high level category.
		- **subtype:** specific to one file type within the "type".
			- **x- subtype prefix:** it means that it's non-standard, i.e. not registered with the IANA.
			- **vnd. subtype prefix:** it means that the MIME value is vendor specific.
		- **Examples:** application/xml or application/vnd.myapp.client+xml
	- **Note:** A MIME type is usually paired with its own, relative file extension (like .xml).
- **Format Choice:** A client can optionally chose the format of the resource using the request header “Accept:”
	- Example

> GET /clients/1234
HTTP/1.1
Host: www.myapp.com
Accept: application/vnd.myapp.client+xml

### Stateless Communication

- Just like the HTTP protocol it’s based on, REST is stateless, meaning there is no memory of the transactions, and that every exchange must have no direct effect on the following ones.
- This allows the server and its web service to be light and performant, but also easily scalable and fault tolerant.
- This also precludes any session tracking or recovery, and any kind of data synchronization with the application.
	- (No cookies)
- Of course, if the application needs to keep a memory of the current state, that responsibility falls on the client.
	- In general, stateless communication compels servers and clients to share some responsibilities more carefully.
- **Note: Different Types of State**
	- Stateless communication doesn’t mean a RESTful web service is stateless. There are other states as well:
		- State of the Resources: values of the resources in a certain time. These values can be “CRUDed”.
		- State of the Client: this is a client’s responsibility.
		- State of the Application: it’s the result of the client/server interaction, composed by the state of the client and the state of the server’s resources.

### Links between resources - The HATEOAS Principle

- **HATEOAS Principle:** Hypermedia As The Engine Of Application State.
	- The principle dictates that **all resources ought to be related and reachable via hypertextual links**.
	- In other words, everything a client needs to know about a resource and those correlated to it must be contained in its representation or be reachable via hypertextual links.
		- Example:

> \<order>
  <span>&nbsp;&nbsp;&nbsp;</span>\<number>12345678\</number>
  <span>&nbsp;&nbsp;&nbsp;</span>\<date>01/07/2011\</date>
  <span>&nbsp;&nbsp;&nbsp;</span>\<client ref="http://www.myapp.com/clients/1234" />
  <span>&nbsp;&nbsp;&nbsp;</span>\<articles>
   	<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>\<article ref="http://www.myapp.com/products/98765" />
    <span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>\<article ref="http://www.myapp.com/products/43210" />
  <span>&nbsp;&nbsp;&nbsp;</span>\</articles>
\</order>

- **Navigation as in an FSA:** considering the HATEOAS principle, coupled with the statelessness of REST, navigation in a RESTful Web Service becomes awfully similar to the elaboration of an FSA (Finite State Automaton).
	- Though it’s not often taken full advantage of, this allows the creation of **highly composite and interconnected resources** accessible by clients who are very **loosely coupled** to the server.
  
## REST and Security

- REST inherits automatically the security of the protocol it uses, so either HTTP or, better, HTTPS.
- Further security can be added, but never at the expense of the REST principles, so adding a “session”, as would come to mind, is not allowed, since REST communication must be stateless. What can be done instead?
	- **Alternatives:**
		- **Client and server must continuously share information to recreate and regenerate the session at each interaction.** This will of course come at the expense of performance.
		- **Creating a “session” resource.** In other words a client’s authentication produces a new session resource on the server which the server will check at each client’s request, provided the client keeps sending a URI to identify himself (which the server must provide at the moment of authentication). 
		- **External Security Management:** External services that decentralize the security of a web service like:
			- **OpenID:** Allows a client to present a unique URI which declares their identity. The server will then ask the OpenID provider to confirm the URI’s authenticity by interacting with the client.
			- **OAuth:** TODO
      
## Swagger

- The problem with REST is that there is no universal formalized interface for one's API, unlike SOAP via its WSDL.
- **Swagger is a specification for documenting a REST API.**
- Swagger allows one to describe the structure of the APIs so that machines can read them, and builds interactive and intuitive API documentation.
- It can also automatically generate client libraries for the API in many languages and explore other possibilities like automated testing. Swagger does this by asking the API to return a YAML or JSON that contains a detailed description of the entire API. This file is essentially a resource listing of the API which adheres to the OpenAPI Specification.
- One can write a Swagger spec for their API manually, or have it generated automatically from annotations in the source code. Check swagger.io/open-source-integrations  for a list of tools to generate Swagger from code.

## SOAP vs REST

- SOAP is a protocol, whereas REST is an architectural style (guidelines) based on established protocols.
- SOAP can use different protocols for transport, whereas REST only uses HTTP.
- SOAP (over HTTP) only uses POST, whereas REST makes requests via GET, using in-URI attributes extensively.
- SOAP has more overhead information, whilst REST deals only in HTTP messages, so it only has HTTP’s overhead.
- SOAP requires more bandwidth than REST because of its overhead.
	- HOWEVER REST might require more server CPU time to validate the requests, which on SOAP can be done client-side, thanks to the WSDL. Thus REST might end up being slower than SOAP.
- SOAP has a view of the web centered on the concept of service, whereas REST on the concept of resource.
- This means that SOAP thinks more in terms of RMI instead of access to a resource.
- SOAP could expose custom functions that go beyond REST’s CRUD, though the latter set is most often enough.
- SOAP is more structured and standardized than REST.
- SOAP can define its own security, whereas RESTful services inherit the security of the underlying transport.
	- SOAP is slightly more secure, and it’s often used in banking because the whole envelope can be encrypted customly, plus the whole business logic of the service can be hidden.
	- REST can be as secure as HTTPS.