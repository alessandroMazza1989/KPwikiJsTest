---
title: SOAP
description: Simple Object Access Protocol
published: true
date: 2021-02-22T13:07:05.024Z
tags: 
editor: markdown
dateCreated: 2021-02-22T13:07:05.024Z
---

# SOAP

- **Goals**
1. The usage of SOAP as an applicative protocol 
2. SOAP syntax
3. SOAP Envelope
4. SOAP Header
5. SOAP Body
6. SOAP Fault
- **Tools & Lab**
[Tool: Download SoapUi](https://www.soapui.org/downloads/soapui.html)
[Tool: Soap UI Mock]( https://www.soapui.org/soap-mocking/working-with-mockservices.htm)

---

## Definition and Rules

### Definition

- It’s a **protocol** for exchanging structured information in the implementation of web services.
- It’s basically the format, based on XML only, of the messages that are sent to and from the web service, in accordance to the WSDL document.
- Supports **HTTP**, SMTP, FTP (and JMS).
- Supports SSL and WS-Security.
- Its interface is described via a WSDL-formatted document that is machine-processable.

### Rules

- A SOAP message is an ordinary XML document containing:
	- An **envelope** element that identifies the XML document as a SOAP message;
	- A **header** element that contains header information;
	- A **body** element that contains call and response information;
	- A **fault** element containing errors and status information.
- ⚠️ All the elements above must always be declared in the default namespace for the SOAP envelope:
	- http://www.w3.org/2003/05/soap-envelope/
- ⚠️The default namespace for SOAP encoding and data types must be:
	- http://www.w3.org/2003/05/soap-encoding	
	- A SOAP message has no default encoding so it must be specified.
- A SOAP message must:
	- be encoded with XML;
	- use the SOAP Envelope namespace;
- A SOAP message must not:
	- contain references to DTD;
	- contain any XML processing instructions.
- SOAP request and response messages share the same basic structure, but with different body elements.

## General Structure: Envelope, Header, Body, Fault

![soap_structure.png](/soap_structure.png)

- **soap:Envelope:** root element of a SOAP message.
	- **xmlns:soap:** must always be http://www.w3.org/2003/05/soap-envelope/
	- **soap:encodingStyle:** defines the data types used in the document. 
		- ⚠️This attribute may appear on any SOAP element, and applies to that element and all its children.
		- ⚠️ **A SOAP message has no default encoding** so it must be specified.
- **soap:Header:** (OPTIONAL) contains application-specific information (like authentication, payment, etc.).
	- ⚠️All immediate child elements must be namespace-qualified.
	- **SOAP:Header Subelements’ Attributes**
		- **soap:mustunderstand:** can be used to indicate whether a header entry is mandatory or optional for the recipient to process. If it’s 1 and the receiver does not recognize the element it will fail immediately.
		- **soap:actor:** used to address the Header element to a specific endpoint when some parts of the SOAP message are intended for some intermediate endpoints on its path to its final endpoint.
		- **soap:encodingStyle:** just as described for the soap:Envelope element.
- **soap:Body:** (REQUIRED) contains the actual SOAP message intended for the ultimate endpoint of the message.
	- ⚠️Immediate child elements of it may be namespace-qualified.
	- **xmlns:tns:** (OPTIONAL) Recall here the target-NS used in the WSDL to access the custom types.
	- **soap:Fault:** (OPTIONAL) used to hold errors and status information in error messages.
		- ⚠️It can only appear once in a SOAP message, as a child of soap:Body.
		- **SOAP:Fault Possible Subelements**
			- **faultcode:** A code for identifying the fault.
				- **Fault Codes**
					- **VersionMismatch:** Found invalid namespace for the soap:Envelope.
					- **MustUnderstand:** An immediate child element of soap:Header, with the mustUnderstand attribute set to "1", was not understood.
					- **Client:** Message incorrectly formed or contained incorrect information.
					- **Server**: Problem with the server so the message could not proceed.
			- **faultstring:** A human readable explanation of the fault.
			- **faultactor:** Information about who caused the fault to happen.
			- **detail:** Holds application specific error information related to the Body element.
      
## SOAP Messages Over HTTP

- The SOAP specification defines the structure of the SOAP messages, not how they are exchanged. This gap is filled by what is called "SOAP Bindings",  which provide bindings for common transport protocols, such as HTTP or SMTP.
	-⚠️**HTTP POST:** SOAP messages are only to be carried via the POST HTTP method, which allows the client to send large amounts of information, which the SOAP envelope is.
	- **Note:** Although it has become standard practice, this use of HTTP is, in a sense, improper, because HTTP is an application-level protocol, but we are here using it as if it were a transport-layer protocol.
	- **Reminder:** Standard HTTP Request/Response Example ( → see Networking notes for more info on HTTP)
  
|                                             Request                                             	|                        OK Response                        	|              KO Response             	|
|:-----------------------------------------------------------------------------------------------:	|:---------------------------------------------------------:	|:------------------------------------:	|
| POST /item HTTP/1.1<br>Host: 189.123.255.239<br>Content-Type: text/plain<br>Content-Length: 200 	| 200 OK<br>Content-Type: text/plain<br>Content-Length: 200 	| 400 Bad Request<br>Content-Length: 0 	|

- **SOAP HTTP Headers **
	- **Content-Type:** defines the message’s MIME type and character encoding (OPTIONAL) used for the XML body of the request or response.
		- **Syntax:** Content-Type: MIMEType; charset=character-encoding
	- **Content-Length:**  specifies the number of bytes in the body of the request or response..
		- **Syntax:** Content-Length: bytes
	- **SOAPAction:** URI of the action to perform. 
		-	Lets the WS application understand which action, defined in the WSDL, to perform. 
		- URI taken from the WSDL attribute in \<service> \<port> \<soap:address location=”URI”...
		- **Syntax:** SOAPAction: http://example.com/WSApplicationLocation
	- Example

|                  POST /item HTTP/1.1                 	|
|:----------------------------------------------------:	|
| Content-Type: application/soap+xml; charset=utf-8    	|
| Content-Length: 250                                  	|
| SOAPAction: http://example.com/WSApplicationLocation 	|

### Example of a SOAP message over HTTP

|                                                                                                                                                                                                                                       SOAP Request                                                                                                                                                                                                                                      	|                                                                                                                                                                                                                           SOAP Response                                                                                                                                                                                                                          	|
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| POST /InStock HTTP/1.1<br>Host: www.example.org<br>Content-Type: application/soap+xml; charset=utf-8<br>Content-Length: nnn<br><?xml version="1.0"?><br><soap:Envelope<br>    xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"<br>    soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding"><br><soap:Body xmlns:m="http://www.example.org/stock"><br>  <m:GetStockPrice><br>    <m:StockName>IBM</m:StockName><br>  </m:GetStockPrice><br></soap:Body><br></soap:Envelope> 	| HTTP/1.1 200 OK<br>Content-Type: application/soap+xml; charset=utf-8<br>Content-Length: nnn<br><?xml version="1.0"?><br><soap:Envelope<br>    xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"<br>    soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding"><br><soap:Body xmlns:m="http://www.example.org/stock"><br>  <m:GetStockPriceResponse><br>    <m:Price>34.5</m:Price><br>  </m:GetStockPriceResponse><br></soap:Body><br></soap:Envelope> 	|