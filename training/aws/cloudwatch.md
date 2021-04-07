---
title: Amazon CloudWatch
description: 
published: true
date: 2021-04-07T13:17:33.981Z
tags: aws, cloud, logs, observability, cloudwatch
editor: markdown
dateCreated: 2021-03-08T14:12:25.350Z
---

# Amazon CloudWatch

**CloudWatch** è il servizio tramite il quale è possibile monitorare le risorse AWS e le proprie applicazioni real-time. E’ possibile collezionare **metriche**, creare **allarmi**, effettuare modifiche alle risorse sulla base di regole definite.

E’ possibile specificare **parametri** per una metrica relativamente a un periodo di tempo prestabilito e configurare **allarmi e azioni automatiche** quando una soglia viene raggiunta (es.: invio notifica verso **SNS** o **AutoScaling**).

CloudWatch offre due piani di monitoraggio:
-  Basic: invia dati di monitoraggio ogni 5 minuti su un set limitato di metriche predefinite, gratuitamente;
-  Detailed: invia dati di monitoraggio ogni minuto e consente aggregazioni sui dati a livello di AZ, mai di region, e non a titolo gratuito;

AWS offre un insieme abbastanza dettagliato di **metriche**, ma è possibile definirne anche di **custom**, basate cioè su eventi su cui AWS non ha visibilità (es.: su consumo di memoria EC2 o disco utilizzato, che sono disponibili al sistema operativo di EC2 e non ad AWS).


CloudWatch Logs può essere utilizzato per monitorare, memorizzare, e accedere ai file di log delle risorse AWS.

Per collezionare log su CloudWatch, è disponibile un **agent** che in automatico invia i log verso CloudWatch.
Va installato sulle istanze (Amazon Linux o Ubuntu).

CloudWatch ha qualche limite da tenere in considerazione:
- 5000 allarmi per account;
- dati sulle metriche memorizzati 2 settimane di default (se si vogliono tenere di più vanno spostati su S3 o Glacier);

## References
- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html