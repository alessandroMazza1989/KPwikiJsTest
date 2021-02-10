---
title: OSI Model
description: Open Systems Interconnection model
published: true
date: 2021-02-10T15:58:41.657Z
tags: 
editor: markdown
dateCreated: 2021-02-10T15:58:41.657Z
---

# OSI Model

> “**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing”
{.is-info}

![osi_model.png](/osi_model.png)

- A note on Session and Cookies: Cookies and Sessions can store information.
	- **Session: (stored both client-side and server-side) [Session-Layer]**
		- A session creates a file in a temporary directory on the server where registered session 						variables and their values are stored. This data will be available to all pages on the site 				during that visit. A session ends when the user closes the browser or after leaving the site, 			the server will terminate the session after a predetermined period of time, commonly 30 minutes 			duration.
		- Only one session per user. Can store anything. 
			- JS: HTTPSession object = request.getSession()
	- **Cookies: (stored only client-side) [Application-Layer]**
		- Cookies are text files stored on the client computer used for session-tracking. The server 					sends a set of cookies to the browser: for example name, age, or identification number etc. The 			browser stores this information on a local machine for future use. The next time the browser 				sends any request to the web server alongside cookies information, the server can identify the 				user.

---
^1^ TCP: Transmission Control Protocol
^2^ UDP: User Datagram Protocol