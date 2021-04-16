---
title: Lab 5
description: 
published: true
date: 2021-04-16T08:07:45.187Z
tags: 
editor: markdown
dateCreated: 2021-04-08T14:19:22.145Z
---

# Consul for Service
The files to test the application are available at the following link: https://drive.google.com/open?id=1qNOhP32QhkqHu4klNpmkfr-V_A03w3Kb

Link containing the description of the BW application: https://community.tibco.com/wiki/integration-between-tibco-businessworkstm-container-edition-and-consul-service-discovery-and

Getting Consul container
```
docker pull progrium/consul
```
Running the container
```
docker run -p 8400:8400 -p 8500:8500 -p 8600:53/udp -h node1 progrium/consul -server -bootstrap -ui-dir /ui
```
We publish 8400 (RPC), 8500 (HTTP), and 8600 (DNS) so you can try all three interfaces. We also give it a hostname of node1. Setting the container hostname is the intended way to name the Consul Agent node.

To connect to the Consul GUI: http://hostIPaddress:8500

![lab5.1.png](/bwce/lab5.1.png)

From the GUI it is possible to create the KEY / VALUE to characterize the module properties 

Running Service images & Testing:
```
docker run -P -e APP_CONFIG_PROFILE=default 
-e CONSUL_SERVER_URL=http://IPConsulContainer:8500 [image_name]
```

