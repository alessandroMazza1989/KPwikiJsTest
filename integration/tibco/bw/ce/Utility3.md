---
title: 3.3
description: 
published: true
date: 2021-04-16T08:18:12.065Z
tags: 
editor: markdown
dateCreated: 2021-04-09T07:18:07.341Z
---

# Networking
Useful Links: https://docs.docker.com/engine/tutorials/networkingcontainers/

Even at the networking level, containers are in some ways isolated.

![utility-1.png](/bwce/utility-1.png)

Docker includes support for networking containers through the use of network drivers. By default, Docker provides two network drivers for you, the bridge and the overlay drivers. You can also write a network driver plugin so that you can create your own drivers but that is an advanced task.

Each Docker Engine installation automatically includes three default networks:

![utility-2.png](/bwce/utility-2.png)

The network called bridge is a special network. Unless a user-defined bridge is specified, Docker always launches containers on this network.

It is possible to inspect the network to obtain the IP address of the containers that are part of it, through the command:
```
docker network inspect [nome_network]
```
Or inspect the info of a container directly
```
docker inspect [container_id]
```
In addition, it is possible to navigate inside a container
```
docker exec -it [container_id] /bin/bash
```
