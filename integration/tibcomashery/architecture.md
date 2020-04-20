---
title: Architettura
description: 
published: true
date: 2020-04-17T16:24:47.248Z
tags: mashery, tibco, architecture
---

## Architettura di Mashery
I macro-componenti principali di Mashery sono:
- Control Center
- Developer Portal
- Mashery API
- Gateway

### Control Center
Il Control Center (CC per brevità) è un portale web dedicato alla configurazione e amministrazione di tutti gli oggetti/risorse necessari al funzionamento del gateway. Questi comprendono le API stesse (detti anche servizi), i package e plan, utenti e ruoli, chiavi d'accesso e altro. Gli oggetti stessi verranno trattati in dettaglio più avanti. Oltre a questo il CC permette anche la consultazione dei report di utilizzo dei servizi esposti sul gateway

### Developer Portal
Il Developer Portal (o dev portal) è un portale web dedicato agli utenti finali, cioè agli sviluppatori, che vogliono accedere alle API esposte dal gateway. Il portale permette di registrarsi, consultare la documentazione relativa ai servizi, testarli tramite swagger, farsi assegnare delle chiavi di accesso, chiedere informazioni o supporto.

### Mashery API
L'API di prodotto Mashery permette di effettuare operazioni di tipo CRUD (Create Read Update Delete) su quasi tutti gli oggetti/risorse del gateway. In questo modo è possibile eseguire programmaticamente la stragrande maggioranza delle le operazioni amministrative disponibili sul CC. Esistono due versioni di questa API (V2 e V3) ma la V3 è quella più moderna e più facilmente utilizzabile poiché segue il paradigma REST. La V2 ha un metodo di autenticazione alquanto bizantino; permette tuttavia di agire con un'unica chiamata su attributi relativi a risorse diverse (supporta un linguaggio simil-SQL) quindi esistono dei casi limite in cui può essere più efficace della V3.

### Gateway
Il gateway vero e proprio è costituito dai seguenti componenti:

- Traffic Manager (TM): il proxy che si occupa dell'instradamento delle chiamate. Nella realtà sono eseguiti più TM in parallelo per meglio gestire il traffico.
- Cassandra Registry: un DB nosql che Mashery utilizza per tenere traccia della topologia dei suoi componenti interni.
- MySQL DB: qui vengono persistite tutte le configurazioni e gli oggetti gestiti dal CC o dalla Mashery API e necessari al funzionamento del gateway.
- Memcached: questo componente si occupa dell'eventuale caching delle risposte ai servizi e di mantenere in cache le configurazioni alle quali è necessario un accesso veloce e ricorrente da parte dei TM (ad esempio le chiavi d'accesso).
- Log Service: basato su fluentd, si occupa dell'accentramento di tutti i log provenienti dagli altri componenti e dell'eventuale instradamento a piattaforme esterne di log management (elastic, splunk, ...).
- Cluster Manager: da questo componente è implementata ed esposta l'API di prodotto, oltre a questo mette a disposizione una command line per operazioni amministrative di basso livello.

## Deployment
Mashery può essere deployato in tre diverse modalità: 
- **Cloud**
- **Local Hybrid**
- **Local untethered**

### Cloud

### Local Hybrid

### Local Untethered