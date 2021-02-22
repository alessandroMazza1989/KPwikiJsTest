---
title: WSDL
description: Web Services Description Language
published: true
date: 2021-02-22T12:49:52.792Z
tags: 
editor: markdown
dateCreated: 2021-02-22T12:49:52.792Z
---

# WSDL

- **Goals**
1. wsdl elements (types, message, operation, portType, binding)
2. Definition of data types using xml schema
3. Definition of messagges
4. Definition of operations
5. Definition of portType
6. Definition of binding
7. abstract wsdl vs concrete wsdl
- **External Links**
[w3 school xml_services](https://www.w3schools.com/xml/xml_services.asp)
[guide to web services](http://www.html.it/guide/guida-web-service/)
[wsdl HelloWorld sample](https://www.tutorialspoint.com/wsdl/wsdl_example.htm)

---

## Definition

- A WSDL is an XML language for describing a web service, specifically its interface (meaning its available functions) and its location.
- Pronounced often as “wisdle”.

## General Structure: types, message, portType, (binding), (service)

![wsdl_definition.png](/wsdl_definition.png)

## Operations

- They correspond to function calls or methods.
	- ⚠️ Multiple inputs/outputs are bundled into the same message. So there is always only ONE of each tag.
- **Operation Types**
	- **ONE-WAY:** The operation can receive a message but will not return a response. Example:
  ![wsdl_oneway.png](/wsdl_oneway.png)
	- **REQUEST-RESPONSE:** The operation can receive a request and will return a response. Example:
  ![wsdl_reqreply.png](/wsdl_reqreply.png)
	- **SOLICIT RESPONSE:** The operation can send a request and will wait for a response.
	- **NOTIFICATION:** The operation can send a message but will not wait for a response.
  
## Bindings

### SOAP Bindings Over HTTP 

There are two kinds of binding elements: one in the WSDL namespace, and one in the SOAP namespace.
- **Example 1:** “document” style for I/O operation.

- **Example 2:** “rpc” style for input-only operation.

- **Elements and Attributes**
	- **binding:** connects a port type to a protocol and data format.
		- Protocol can be SOAP (**soap:binding**) or simple HTTP (**http:binding**)
		- **name:** arbitrary.
		- **type:** the name of the \<portType> element.
	- **soap:binding**
		- **style:** can be “rpc” or “document”.
			- **rpc:** best used for messages that contain parameters or returned values.
			- **document:** best used for messages that contain documents
				- ⚠️Requires adjustments to be made in the **\<soap:body>** elements (see elsewhere).
		- **transport:** defines the soap protocol to use. In this case HTTP.
	- **operation:** defines each operation the portType exposes through the binding.
		- **soap:operation:** for each operation the corresponding SOAP action has to be defined. 
			- **soapAction:** this is the actual SOAP action that will be performed. 
				- It refers to the actual piece of code that will be run.
			- **style:** confirm the chosen style for the soap:binding.
		- **input/output/fault:** each contains a <soap:body> element.
			- **soap:body:** says how the message parts will appear in the actual SOAP body.
				- **use:** defines if the input and output are encoded and how.
					- **literal:** without encoding.
					- **encoded:** with encoding.
						- Requires attribute encodingStyle. 
							- i.e.: http://schemas.xmlsoap.org/soap/encoding/
              
### SOAP Bindings Over JMS 

TODO: See how to create a SOAP binding over JMS

## Service Definition

- **Example:** SOAP service binding.
	![wsdl_service_description.png](/wsdl_service_description.png)
- **Elements and Attributes**
	- **service:** is a collection of ports
		- **port:**  (also referred to as endpoints) are comprised of a binding and a network address.
			- **soap:address location:** Actual URI of the WS application that will process the message.
      
## Abstract vs Concrete WSDL

- **Abstract WSDL:** describes what the WS does, but not how it does it or how to contact it. **\[Definitions only]**
	- **It defines only:**
		- the operations provided by the WS.
		- the input, output and fault messages used by each operation of the WS, and their format.
	- **Elements: definition, types*, messages, portType, part, operation.**
		- Import statements of XSDs make the WSDL necessarily abstract until the XSD types are actually parsed and imported.
- **Concrete WSDL:** adds information about how the WS communicates and where you can reach it. **\[Implementation]**
	- **It adds:**
		- the communication protocols and data encodings used by the WS.
		- the port address that must be used to contact the WS.
	- **Elements: binding, service, port.**

## WSDL Structure Summary Graph with SOAP Embedding

![wsdl_graph.png](/wsdl_graph.png)

## Example of a concrete WSDL fragment bound with SOAP over HTTP

![wsdl_concrete.png](/wsdl_concrete.png)

## A Note on URLs

- If the server supports it, a web service’s URL can often be used to summon the service’s WSDL directly, instead of having to ask for it, by adding ‘**?WSDL**’ at the end of the URL. For example:
	- http://webservices.oorsprong.org/websamples.countryinfo/CountryInfoService.wso?WSDL
		- Without the ‘**?WSDL**' in this case you would simply access the web application’s HTML page.