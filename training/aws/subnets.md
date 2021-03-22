---
title: Subnets
description: 
published: true
date: 2021-03-22T08:06:43.082Z
tags: aws, cloud, networking, security, subnets
editor: markdown
dateCreated: 2021-03-08T10:04:59.321Z
---

# Subnets

Una subnet è un segmento di una VPC in cui è possibile lanciare istanze EC2, RDS e altre risorse AWS.

Le subnet sono definite dai **CIDR blocks** (es.: 10.0.1.0/24 e 192.168.0.0/24). La subnet più piccola che è possibile creare è una /28 (16 IP addresses). 
AWS **si riserva** per scopi interni 5 indirizzi IP per ogni blocco.

Dopo aver creato una VPC, è possibile aggiungere una o più subnets in ogni Availability Zone. Una subnet **risiede sempre all’interno di una Availability Zone** e non può espandersi tra più zone. Una subnet quindi appartiene sempre ad una sola Availability Zone. 
Ovviamente, possono esserci diverse subnet all’interno di una AZ.

Le subnet possono essere classificate come:
- **Pubbliche**: la route table associata dirige il traffico della subnet verso l’IGW della VPC; 
- **Private**: la route table associata NON dirige il traffico della subnet verso l’IGW della VPC;
- **VPN-only**: la route table associata dirige il traffico della subnet verso il VPG della VPC e non esistono rotte verso l’IGW;

Indipendentemente dalla tipologia, gli indirizzi IP di una subnet **sono sempre privati**.
La VPC di default contiene una subnet pubblica in ogni Availability Zone di ogni singola region, con una netmask di /20.

## References
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html