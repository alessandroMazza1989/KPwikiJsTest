---
title: Network Rules
description: Classless/Classful Routing and Subnets
published: true
date: 2021-02-10T16:16:02.925Z
tags: 
editor: markdown
dateCreated: 2021-02-10T16:15:12.703Z
---

# Network Rules

### CIDR: Classless Inter-Domain Routing

- **Address partitioning:**
	- Net-ID = n bit
 	- Host-ID = 32 - n bit
- **Syntax:**

|   Address   	| Mask (bits of the Net-ID) 	|
|:-----------:	|:-------------------------:	|
| 134.76.96.0 	|            /19            	|

- **Netmask:** it’s the dotted notation of the mask

| Mask 	|                  Binary Mask                  	|    Netmask    	|
|:----:	|:---------------------------------------------:	|:-------------:	|
|  /24 	| 1111 1111 . 1111 1111 . 1110 0000 . 0000 0000 	| 255.255.224.0 	|

- In this case there are **32 - 19 = 13** bits for the Host-ID:
	- 2^13^= 8192 host addresses for each Net-ID.
		- So, from the address **134.76.96.0** to which **last_address**?
			- 8192 / 256 = 32
			- 32-1 = 31 increments of the third byte, so 96 + 31 = 127
			- fourth byte will reach 255
			- Therefore: **last_address = 134.76.127.255**
- **Special Addresses: 2 addresses (the 1st and last) per every subnet are reserved!**

|  NETWORK ADDRESS<br>HOST-ID with all 0 	| First address in the subnet.<br>Used only in routing tables.        	|
|:--------------------------------------:	|---------------------------------------------------------------------	|
| DIRECT BROADCAST<br>HOST-ID with all 1 	| Last address in the subnet.<br>Reaches everyone in the subnet.      	|
|  LIMITED BROADCAST<br>255.255.255.255  	| All ones.<br>Reaches everyone, but it doesn’t go beyond the router. 	|
|            NET-ID with all 0           	| Identifies the host (ex: 0.0.21.173/16)                             	|
|                 0.0.0.0                	| Identifies the sender (when it doesn’t know it’s own address).      	|
|                127.x.y.z               	| Loopback Address                                                    	|
- **VLSM:** Variable Length Subnet Mask: See paper example on notes.
