---
title: DNS
description: Domain Name System
published: true
date: 2021-02-10T16:07:38.223Z
tags: 
editor: markdown
dateCreated: 2021-02-10T16:07:38.223Z
---

# DNS

- DNS is the hierarchical organization of name servers which pairs URLs to IP addresses.
- DNS requests and responses are carried over UDP.
- DNS Query Types:
	- **Iterative:** when any following queries are handled directly by the machine making 										the query.
		- From the LNS (Local Name Server) and on the queries are iterative.
	- **Recursive:** when any following queries are handled by other nodes further down the 									line.
		- From client to LNS the queries are recursive.
    
- **Symbolic-name resolution algorithm and DNS message Structure**

![dns.jpg](/dns.jpg)
![dns2.png](/dns2.png)

-	**Local Name Servers (LNS):** They are the first nodes, and are directly connected to the 																routers.
- **Authoritative Name Servers:** They offer an update mechanism for developers to manage 																	their public names. They are the place where the actual 																	IP addresses are resolved.
- **Caching:** A server can keep authoritative information cached for a certain TTL, 										defined by the authoritative server. TLD (Top Level Domain) servers are also 							kept in memory for another TTL in the LNSs. The TTL is decided by the LNSs.

- **DNS Information:** Stored as resource records.
	- **Resource Records (RR):** Pairing data stored in the DNS servers.
		- **Types:**
			- **A →** Name is the name of the host and Value is its IP address.
			- **NS →** Name is a domain and Value the name of a server that has pertinent info.
			- **CNAME →** Name is an alias for a host whose name is actually Value.
			- **MX →** Name is a mail domain and Value the name of the mail server.

- **Adding a domain to a DNS network:**
	- Contact a DNS Registrar and provide it with your symbolic names and IP addresses of 			the Authoritative Name Servers.
	- **Example:** Hello wants to register hello.com
		- The DNS Registrar will have to add 2 Resource Records:
			- hello , dns1.hello.com , NS
			- dns1.hello.com , 212.212.212.1 , A