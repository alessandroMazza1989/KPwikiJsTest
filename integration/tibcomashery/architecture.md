---
title: Architettura
description: 
published: true
date: 2020-04-21T14:39:40.851Z
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
Il gateway vero e proprio è il motore di Mashery ed è *container based*. Ciò significa che ogni componente risiede in un container Docker dedicato. Un container Docker può essere visto, semplificando, come una piccola Virtual Machine con un overhead molto ridotto. I container sono per loro stessa natura effimeri e rapidamente sostituibili e devono essere gestiti da un orchestratore (eg. Kubernetes, Swarm, OpenShift, ...) andando a formare un *cluster*. È possibile, e consigliato, replicare ogni container all'interno del cluster in modo da garantire robustezza e parallelismo. Il dimensionamento dell'infrastruttura richiede considerazioni relative al volume di traffico previsto e a eventuali picchi, alle risorse hardware disponibili e al loro costo, alla ridondanza geografica, ecc.

Di seguito l'elenco dei container/componenti di Mashery:

- Traffic Manager (TM): il proxy che si occupa dell'autenticazione, elaborazione e instradamento delle chiamate. Di gran lunga il componente più importante poiché è quello che direttamente eroga il servizio verso i client.
- Cassandra Registry: un DB nosql che Mashery utilizza per tenere traccia della topologia dei suoi componenti interni e, in caso di installazione distribuita geograficamente, sincronizzarla tra le diverse zone.
- MySQL DB: qui vengono persistite tutte le configurazioni e gli oggetti gestiti dal CC o dalla Mashery API e necessari al funzionamento del gateway.
- Memcached: si occupa del caching opzionale delle risposte ai servizi e di mantenere in cache le informazioni per le quali è richiesto un accesso veloce e ricorrente da parte dei TM (ad esempio le chiavi d'accesso).
- Log Service: basato su fluentd, si occupa dell'accentramento di tutti i log provenienti dagli altri componenti e dell'eventuale instradamento a piattaforme esterne di log management (elastic, splunk, ...).
- Cluster Manager: espone l'API di prodotto e mette a disposizione una command line per operazioni amministrative a basso livello.

**NB**: le considerazioni fatte in questo paragrafo valgono ufficialmente per un'installazione local di Mashery. Non esiste documentazione sul funzionamento interno del Gateway in modalità cloud tuttavia possiamo presumere con una certa dose di sicurezza che non si discosti affatto da quanto scritto.
## Deployment
Mashery può essere deployato in tre diverse modalità: 
- **Cloud**
- **Local Hybrid**
- **Local Untethered**

Tibco considera Mashery in modalità *Cloud* quasi come fosse un prodotto separato ([*Tibco Cloud Mashery*](https://docs.tibco.com/products/tibco-cloud-mashery)) categorizzandolo come uno dei tanti servizi messi a disposizione nella sua offerta cloud. Analogamente la modalità *Local* ([*Tibco Mashery Local*](https://docs.tibco.com/products/tibco-mashery-local-5-3-0)) ha documentazione e supporto dedicati. Ciò non toglie che sotto al cofano Mashery è un'unica piattaforma e un cliente può benissimo utilizzare il prodotto contemporaneamente in entrambe le modalità con la stessa sottoscrizione (a patto che abbia le opportune licenze).

### Cloud
In modalità cloud tutti i componenti del gateway sono deployati sul cloud e la gestione della piattaforma è completamente delegata a Tibco. L'amministratore si occupa unicamente della configurazione del gateway e delle API.
Questa modalità ha come punto di forza l'assenza di overhead per la gestione ad parte del cliente, tuttavia occorre tenere presente che:

1. Occorrerà stabilire un canale di comunicazione sicuro e privato (VPN) e/o autenticare tutte le comunicazioni tra il cloud Tibco e i backend del cliente.
2. Il flusso dati transita su di un cloud in gestione a una società esterna, Tibco. Ci sono clienti (ad esempio banche o società appaltatrici dell'esercito) per cui la riservatezza e le limitazioni contrattuali sulla locazione geografica dei dati non consentono l'utilizzo di strumenti cloud.
### Local Hybrid
In modalità ibrida, anche detta tethered (dall'inglese *tether*: "corda, collegamento") il componente Gateway viene installato e gestito dal cliente in locale. Vale la pena sottolineare che *Local* non significa necessariamente *on-premises*: un'installazione Mashery può benissimo risiedere su un'area cloud privata e viene comunque definita *Local* e non *Cloud*.
I restanti componenti (CC, Dev Portal, API di prodotto) continuano a essere in gestione a Tibco. Si rende necessaria una sincronizzazione costante tra la parte local e quella cloud (essenzialmente l'ambiente locale recepisce le configurazioni effettuate sul CC e l'ambiente cloud riceve aggiornamenti sulle statistiche d'uso delle API esposte). La comunicazione in entrambe le direzioni avviene unicamente tramite interrogazioni dal local a un servizio cloud dedicato (il MOM, *Mashery On-Prem Manager*).

### Local Untethered
In modalità untethered tutti i componenti vengono installati e gestiti esclusivamente in locale. Ci sono alcune variazioni di nomenclatura dei componenti (eg: il Control Center locale viene chiamato *Configuration Manager* mentre il Developer Portal per distinzione diventa *Local Developer Portal*) e alcune funzionalità dei portali cloud sono diverse e/o assenti. Non c'è comunicazione alcuna con il MOM.

**NB**: le modalità Hybrid e Untethered sono mutualmente esclusive e la scelta viene fatta in fase di installazione di Mashery Local.