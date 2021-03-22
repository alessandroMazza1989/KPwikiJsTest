---
title: Security Groups
description: 
published: true
date: 2021-03-22T08:28:32.276Z
tags: aws, cloud, networking, security, security groups
editor: markdown
dateCreated: 2021-03-08T10:07:33.357Z
---

# Security Groups

Un security group è **un firewall virtuale** che controlla le regole inbound e outbound da e verso le risorse AWS. 

Tutte le istanze EC2 _devono essere lanciate all’interno di un security group_. Se non viene specificato, AWS ne crea un nuovo e lo assegna all’istanza, oppure associa l’istanza al security group di default.

Il security group di **default**:
- consente le comunicazioni **tra tutte le risorse all’interno dello stesso security group**;
- consente il traffico in **uscita**;
- **vieta tutto il resto del traffico**;

Da ricordare:

- Per ogni VPC possono essere creati fino a 500 security groups;
- E’ possibile aggiungere fino a 50 regole inbound e 50 regole outbound per ogni security group. Se si ha bisogno di più di 100 regole, è possibile associare fino a 5 security group ad una network interface;
- E’ possibile specificare **solo allow rules e no deny rules** (differenza importante rispetto alle ACLs);
- Di **default**, _non è consentito_ alcun traffico **inbound**;
- Di **default**, il **traffico outbound** è _consentito_;
- I security group sono **stateful**, il che significa che eventuali _risposte a traffico in uscita sono permesse_ indipendentemente dalle regole di inbound e viceversa (differenza importante rispetto alle ACLs);
- Le istanze associate allo stesso security group _non possono parlare tra loro_ fino a che non si **esplicita** (con l’eccezione del default security group);
- I security group possono essere **modificati in qualsiasi momento** e associati o meno alle varie istanze in qualsiasi momento. Le modifiche hanno effetto da **subito**;

## References
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html