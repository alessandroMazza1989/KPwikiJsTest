---
title: Network Elements
description: Routing Table, Network Devices, Bridge, NAT, Firewall
published: true
date: 2021-02-10T16:36:45.690Z
tags: 
editor: markdown
dateCreated: 2021-02-10T16:36:45.690Z
---

# Network Elements

## Routing Table

- **Simplified Structure:**

| Network Destination 	| Netmask 	|    Next Hop    	|
|:-------------------:	|:-------:	|:--------------:	|
|    192.168.1.128    	|   /27   	|  192.168.1.213 	|
|    192.168.1.192    	|   /28   	| Direct Forward 	|
|       0.0.0.0       	| 0.0.0.0 	|   192.168.1.0  	|

- **Actual Structure:**
	- **Network Destination + Netmask:** These describe the Net-ID
	- **Gateway:** This is the Next Hop
	- **Interface:** Which locally available interface is responsible for reaching the 												gateway.
	- **Metric:** it’s the associated cost of using the indicated route (minimum number of 									hops usually).

| Network Destination 	|    Netmask    	|    Gateway    	|   Interface   	| Metric 	|
|:-------------------:	|:-------------:	|:-------------:	|:-------------:	|:------:	|
|     132.168.0.0     	| 255.255.255.0 	| 192.168.0.100 	| 192.168.0.100 	|   10   	|

- **Default Gateway:** serves as an access point or IP router that a networked computer uses to send information to a computer in another network or the Internet.
- **Address Elimination:** If the destination address has the same next-hop as the Default Gateway, then it can be eliminated from the routing table.
- **Address aggregation:** The lines with contiguous addresses and same next-hop are merged.
	- Aggregation is achieved by defining a supernet, by shortening the netmask accordingly.
	- If one of the contiguous-destination addresses has a different next-hop, aggregation can still happen for the others, but that one is kept as is.
	- If one of the contiguous-destination addresses is missing, aggregation can still happen, but a line must be added for the missing destination address with next-hop the default gateway.

## Network Devices

- **REPEATER:**  A repeater operates at the physical layer. Its job is to regenerate the signal over the same network before the signal becomes too weak or corrupted so as to extend the length to which the signal can be transmitted over the same network. An important point to be noted about repeaters is that they do not amplify the signal. When the signal becomes weak, they copy the signal bit by bit and regenerate it at the original strength. It is a 2 port device.
- **HUB:** A hub is basically a multiport repeater. A hub connects multiple wires coming from different branches. Hubs cannot filter data, so data packets are sent to all connected devices. They also do not possess any shortest-path algorithms. A hub is a multi-port device.
- **BRIDGE:** A bridge operates at the data link layer. A bridge is a repeater, with add on the functionality of filtering content by reading the MAC addresses of source and destination. It is also used for interconnecting two LANs working on the same protocol. It has a single input and single output port, thus making it a 2-port device.
- **SWITCH:** A switch is a multiport bridge with a buffer and a design that can boost its efficiency (a large number of ports imply less traffic) and performance. A switch is a data link layer device. The switch can perform error checking before forwarding data.
- **ROUTER:** A router is a device like a switch that routes data packets based on their IP addresses. Router is mainly a Network Layer device. Routers normally connect LANs and WANs together and have a dynamically updating routing table based on which they make decisions on routing the data packets (NAT).
- **GATEWAY:** A gateway, as the name suggests, is a passage to connect two networks together that may work upon different networking models. They basically work as the messenger agents that take data from one system, interpret it, and transfer it to another system. Gateways are also called protocol converters and can operate at any network layer. Gateways are generally more complex than switch or router.

![network_devices.jpg](/network_devices.jpg)

## Bridged and NAT networking

- **NAT: Network Address Translation - Higher OSI level**
	- An external address, usually routable, is the "outside" of the NAT. The machines behind the NAT have an "inside" address that is usually non-routable. When a connection is made between an inside address and an outside address, the NAT system in the middle creates a forwarding table entry consisting of (outside_ip, outside_port, nat_host_ip, nat_host_port, inside_ip, inside_port). Any packet matching the first four parts gets its destination re-written to the last two parts. So with NAT the IPs of the virtual machines and the network your host is connecting to are separated. Meaning your VMs are on a different subnet.
	- If a packet is received that doesn't match an entry in the NAT table, then there is no way for the NAT box to know where to forward it unless a forwarding rule was manually defined. That's why, by default, a machine behind a NAT device is "protected".
- **Bridged - Low OSI Level (2)**
	- With a bridged interface your virtual machines are directly connected to the network the network interface they are using is connected to. This means in your case that they will be directly connected to the network your host connects to, getting IP addresses from the DHCP server running on the network.
  
## Firewall

- Involves layers 2 and above.
- **Methodologies and functions:**
	- **Static packet filtering:** Level 3 packet filtering by IP and port.
	- **Stateful packet filtering:** Keeps in mind active TCP streams and some history.
	- **Proxy firewall:** Acts as an intermediary between the original client and the server.
	- **Application Inspection:** Packet inspection with application level understanding.
	- **NAT firewalls:** Used to translate private IP into a public IP to hide the source IP.
	- **Next Gen:** Deep packet inspection.
- **Types:**
	- Host-based (software)
	- Network-based (hardware + software)