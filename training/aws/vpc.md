---
title: Amazon Virtual Private Cloud (VPC)
description: 
published: true
date: 2021-03-18T09:22:01.151Z
tags: aws, cloud, networking, security, vpc
editor: markdown
dateCreated: 2021-03-08T10:04:18.916Z
---

# Amazon Virtual Private Cloud (VPC)

## Amazon VPC

Amazon VPC è il **layer di rete** per Amazon EC2 che consente di costruire delle reti virtuali all’interno di AWS.
E’ possibile controllare vari aspetti di una VPC, compresi il **range di IP addresses**, le **subnets**, configurare le **route tables**, i **network gateways**, e le impostazioni di sicurezza. 
All’interno di una region, è possibile creare diverse VPC: ogni VPC è **logicamente separata** dalle altre.

Quando si crea una VPC si deve specificare il range di indirizzi IPv4 scegliendo un **CIDR (Class Inter Domain Routing)** block, come ad esempio *10.0.0.0/16*.
Il range di indirizzi non può essere modificato una volta che la VPC è stata creata. Come range, le VPC possono andare:

- da un blocco /16 (65,536 indirizzi disponibili) (MAX)
- a un /28 (16 indirizzi disponibili) (MIN)

Gli indirizzi IPv4 di una VPC **non devono sovrapporsi** con quelli di qualsiasi altra VPC con la quale dovrà essere connessa.
Poiché il servizio VPC è stato lanciato dopo il servizio EC2, esistono 2 diverse piattaforme di networking disponibili: 
- EC2-Classic;
- EC2-VPC;

Dal Dicembre 2013 per ogni account AWS EC2 viene creata una **VPC di default** per ogni region, con una **subnet di default** creata in ogni Availability Zone. 
Il blocco CIDR assegnato alla VPC di default è 172.31.0.0/16.

Una VPC consiste delle seguenti componenti:
- **Subnets**;
- **Route tables**;
- **DHCP**;
- **Security groups**;
- **ACLs**;

## References
- https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html