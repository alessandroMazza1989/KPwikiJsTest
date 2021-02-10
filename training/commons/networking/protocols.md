---
title: Network Protocols
description: HTTP, HTTPS, TLS, SSH, SCP, FTP
published: true
date: 2021-02-10T16:55:16.472Z
tags: 
editor: markdown
dateCreated: 2021-02-10T16:49:47.770Z
---

# Network Protocols

## HTTP - HyperText Transfer Protocol

- Application level protocol for the exchange of hypertext documents.
- **HTTP is a stateless protocol:** no client identification, no session, no memory of the transaction.
- **Port (optional):** 	80
- **URL form:**		protocol://www.server_network_address:port/page_path
- **Connection type:** 	TCP/IP	(can be persistent or non persistent)

### Handshake

TO DO

### HTTP Requests

- **Request Commands**
	- **GET:** to get information from the server. The request contains information that describes what the user wants via a query string, passed as a sequence of characters appended to the URL:
		- **Example:** http://my.server/page?par1=val1&par2=val2
			- The ‘?’ indicates parameters with the syntax: name=value
			- Multiple parameters can be concatenated with ‘&’.
			- Whitespaces can only be expressed with ‘%20’ or’+’.
	- **POST:** to send information or an input to the server.
		- The request passes all its data, of unlimited length, as part of its body.
	- **HEAD:** to get information on the document according to the requested header.
	- **PUT:** to save a document on the server (DEPRECATED).
	- **DELETE:** to delete a document from the server at a certain URL.
	- others: **PATCH, TRACE , OPTIONS**.
- **Get or Post?:** GET is simpler and faster than POST, but prefer POST when:
	- A cached file is not an option (update a file or database on the server).
	- Sending a large amount of data to the server (POST has no size limitations).
	- Sending user input, POST is more robust and secure than GET.
- **Request structure:** 
	- full-request :- request-line	*( general-header | request-header | entity-header) 	CRLF	[entity-body]
	- request-line :- method SP URL SP version CRLF
		- Example of request line: GET /pub/papers/pap101.html HTTP/1.0
- **Request headers:** (an incomplete list) (multiple elements are comma-separated)
	-	**accept:** The media type/types acceptable.
		- Example: application/json, text/plain, image/jpeg...
	- **accept-language:** List of acceptable languages.
		- Example: en-US, it-IT
	- **accept-charset:** The charset acceptable.
		- Example: utf-8
	- **cache-control:** Set the caching rules.
		- Example: no-cache
	- **accept-encoding:** List of acceptable encodings.
		- Example: gzip, deflate
	- **user-agent:** The string that identifies the user agent.
	- **host:** The domain name of the server (used to determine the server with virtual hosting), and the TCP port number on which the server is listening. If the port is omitted, 80 is assumed. This is a mandatory HTTP request header.
		- Example: localhost:8080
	- **connection:** Control options for the current connection.
		- Accepts keep-alive and close. Deprecated in HTTP/2
		- Example: keep-alive
	- **cookie:** Cookie name and value.
		- Example: name=value
	- **content-length:** The length of the response body in bytes.
		- Example: 348
	- **date:** The date and time that the message was sent.
		- Example: Date: Tue, 15 Nov 1994 08:12:31 GMT
    
### HTTP Responses

- **Status codes:**
 	- **1xx :** Information
 	- **2xx :** Success
 	- **3xx :** Redirection
 	- **4xx :** Client error
 	- **5xx :** Server error
- **Response structure:** 
	- full-response :- status-line *(	general-header | request-header | entity-header) 	CRLF	[entity-body]
	- status-line :- version SP STATUS SP message CRLF
		- Example of status line: HTTP 404 - File not found
- **Response headers:** (an incomplete list) (multiple elements are comma-separated)
	- **accept-ranges:** What partial content range types this server supports.
		- Example: bytes
	- **age:** The age the object has been in a proxy cache in seconds.
	- **cache-control:** Set the caching rules. Measured in seconds
		- Example: max-age=3600
	- **connection:** Control options for the current connection. Deprecated in HTTP/2
		- Example: keep-alive or close
	- **content-language:** The language the content is in.
	- **content-length:** The length of the response body in octets (8-bit bytes).
	- **content-location:** An alternate location for the returned data.
		- Example: /index.htm
	- **content-type:** The MIME type of this content.
		- Example: text/html; charset=utf-8
	- **date:** The date and time that the message was sent.
		- Example: Date: Tue, 15 Nov 1994 08:12:31 GMT
	- **expires:** Gives the date/time after which the response is considered stale.
		- Example: Date: Tue, 15 Nov 1994 08:12:31 GMT
	- **last-modified:** The last modified date for the requested object in RFC 2822.
		- Example: Date: Tue, 15 Nov 1994 08:12:31 GMT

## HTTPS - HyperText Transfer Protocol Secure

TO DO