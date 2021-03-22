---
title: Elastic Load Balancer
description: 
published: true
date: 2021-03-22T10:23:51.860Z
tags: aws, cloud, networking, security, elastic load balancer, load balancer
editor: markdown
dateCreated: 2021-03-08T10:08:28.825Z
---

# Elastic Load Balancer

Un **load balancer** è un meccanismo che automaticamente **distribuisce** il traffico tra istanze EC2 multiple.

E’ possibile usare il proprio load balancer, installato su un’istanza EC2, oppure utilizzare il servizio **AWS ELB**, che offre **un load balancer gestito** da utilizzare facilmente.

ELB consente di distribuire il traffico verso le istanze EC2 di _una o più AZ_, consentendo di erogare applicazioni ad **alta disponibilità**.

ELB supporta **routing e load balancing** dei protocolli **HTTP, HTTPS, TCP e SSL**.

ELB fornisce un **singolo entry point** per la configurazione del DNS e supporta un bilanciamento **sia Internet-facing che Application-facing**.

ELB supporta gli **health checks** sulle istanze EC2 affinché il traffico non venga inoltrato verso istanze non in salute.

ELB può **scalare automaticamente** sulla base delle metriche che colleziona.

ELB si integra con **AutoScaling** per **scalare automaticamente le istanze EC2** dietro al balancer stesso.

Infine, ELB è sicuro, lavora con VPC per dirigere il traffico internamente tra applicazioni private, **esponendo solo gli IP pubblici** delle applicazioni Internet-facing.

ELB supporta inoltre la **gestione dei certificati SSL**.

## Types of Load Balancers


### Application Load Balancer




## References
- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html