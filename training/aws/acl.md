---
title: Network ACLs
description: 
published: true
date: 2021-03-22T08:44:51.157Z
tags: aws, cloud, networking, security, acl
editor: markdown
dateCreated: 2021-03-08T10:06:25.014Z
---

# Network Access Control Lists (ACLs)

Una ACL è un altro layer di sicurezza che invece è stateless, e agisce a livello di subnet. Una network ACL è cioè una lista numerata di regole che AWS valuta in ordine, partendo dal numero più basso, per determinare se il traffico è consentito da o verso qualsiasi subnet associata con l’ACL.

Le Amazon VPC sono create con una default network ACL associata con ogni subnet che consente tutto il traffico inbound e outbound.

Quando si crea una nuova ACL, essa nega tutto il traffico (in e out) fino a che non vengono create apposite regole. 


| Security Groups | Network ACL |
| --------------- | ----------- |
| Opera a livello di **istanza** (first layer)  | Opera a livello di **subnet** (second layer) |
| Supporta solo **allow rules**  | Supporta **sia allow che deny rules** |
| **Stateful**: il traffico di ritorno è sempre concesso, al di là delle regole impostate | **Stateless**: il traffico di ritorno deve essere permesso |
AWS **valuta tutte le regole** prima di decidere se consentire o meno il traffico | AWS processa le regole **in ordine numerico** |
Sono applicati **selettivamente** alle istanze | Sono applicate **a tutte le istanze di una subnet**.


## References
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html