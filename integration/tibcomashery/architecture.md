---
title: Architettura e Deployment di Mashery
description: 
published: true
date: 2020-04-24T16:16:09.774Z
tags: mashery, tibco, api gateway, architecture, control center, developer portal
---

# Architettura
I macro-componenti principali di Mashery sono:
- [Control Center](#control-center)
- [Developer Portal](#developer-portal)
- [Mashery API](#mashery-api)
- [Gateway](#gateway)

## Control Center
Il [Control Center](http://docs.mashery.com/gettingstarted/GUID-84038256-96F8-47F2-AD86-8EEC424F7BB6.html) (CC per brevità) è un portale web dedicato alla configurazione e amministrazione di tutti gli oggetti/risorse necessari al funzionamento del gateway. Questi comprendono le API stesse (detti anche servizi), i package e plan, utenti e ruoli, chiavi d'accesso e altro. Gli oggetti stessi sono trattati in dettaglio nella sezione dedicata. Oltre a questo il CC permette anche la consultazione dei report di utilizzo dei servizi esposti sul gateway.

>![cc.jpg](/mashery/cc.jpg)
>Homepage del Control Center per un utente avente ruolo di Amministratore d'area

L'indirizzo del CC è [*\<nomeareacliente\>.admin.mashery.com*](http://www.blankwebsite.com/). È anche possibile (o necessario, se si utilizza un'utenza in Single sign-on) raggiungerlo dal sito [*cloud.tibco.com*](https://cloud.tibco.com/) selezionando *APIs → Control Center* dopo essersi autenticati.

>![cloud_homepage.jpg](/mashery/cloud_homepage.jpg)
>Homepage del cloud Tibco

## Developer Portal
Il [Developer Portal](http://docs.mashery.com/manage/GUID-FFE293BA-7DD7-4A3A-9257-3580013733BB.html) (o dev portal) è un portale web dedicato agli utenti finali, cioè agli sviluppatori che vogliono accedere alle API esposte dal gateway. Il portale permette di registrarsi, consultare la documentazione relativa ai servizi, testarli tramite swagger, farsi assegnare delle chiavi di accesso, chiedere informazioni o supporto.

>![dev_portal.jpg](/mashery/dev_portal.jpg)
> Homepage del Dev Portal [developer.pirelli.com](https://developer.pirelli.com/)

>L'indirizzo iniziale del Developer Portal Cloud è [*\<nomeareacliente\>.mashery.com*](http://www.blankwebsite.com/). Una delle prime operazioni in fase di adozione di Mashery è spesso la customizzazione di questo indirizzo: [*developer.\<nomeareacliente\>.com*](http://www.blankwebsite.com/) è generalmente la scelta più popolare.
>
>Esempi di Dev Portal di alcuni clienti Tibco, con diversi gradi di personalizzazione, sono:
> 
> - [developer.pirelli.com](https://developer.pirelli.com/)
> - [developer.sportradar.com](https://developer.sportradar.com/)
> - [developer.battle.net](https://developer.battle.net/)
> - [developer.walmartlabs.com](https://developer.walmartlabs.com/)
> - [developer.fandango.com](https://developer.fandango.com/)
> - [developer.hotelbeds.com](https://developer.hotelbeds.com/)
> - [developer.lufthansa.com](https://developer.lufthansa.com/)
> - [developer.airfranceklm.com](https://developer.airfranceklm.com/)
> - [developer.iairgroup.com](https://developer.iairgroup.com/)
> - [developer.avios.com](https://developer.avios.com/)
{.is-info}


## Mashery API
La [API](https://developer.mashery.com/docs/read/mashery_api) di prodotto Mashery permette di effettuare operazioni di tipo CRUD (Create Read Update Delete) su quasi tutti gli oggetti/risorse del gateway. In questo modo è possibile eseguire programmaticamente la stragrande maggioranza delle operazioni amministrative disponibili sul CC.

>![mashery_api.jpg](/mashery/mashery_api.jpg)
> Parte dello [swagger](https://developer.mashery.com/io-docs) della API V3 di prodotto

> Esistono due versioni della API (V2 e V3) ma la V3 è quella più moderna e più facilmente utilizzabile poiché segue il paradigma REST. La V2 ha un'autenticazione alquanto bizantina; permette tuttavia di agire con un'unica chiamata su attributi relativi a risorse diverse (supporta un linguaggio simil-SQL) quindi esistono casi limite in cui può essere più efficiente della V3.
{.is-info}

>[Qui](/mashery/mashery_api.postman_collection.json) una collection postman per effettuare chiamate all'API.
{.is-info}

## Gateway
Il gateway vero e proprio è il motore di Mashery ed è *container based*. È cioè composto da [componenti separati](https://docs.tibco.com/pub/mash-local/5.3.0/doc/html/GUID-B454FA7F-9A50-488D-AF3C-0DD15E83C7EB.html) eseguiti all'interno di container Docker dedicati. Un container Docker può essere visto, semplificando, come una piccola Virtual Machine con overhead molto ridotto. I container sono per loro stessa natura effimeri e velocemente sostituibili e devono essere gestiti da un orchestratore (eg. Kubernetes, Swarm, OpenShift, ...) andando a formare un *cluster*. 
> È possibile, e consigliato, replicare ogni container all'interno del cluster in modo da garantire robustezza e parallelismo. Il dimensionamento dell'infrastruttura richiede considerazioni relative al volume di traffico previsto e a eventuali picchi, alle risorse hardware disponibili e al loro costo, alla ridondanza geografica, ecc.
{.is-info}

 >![cluster.jpg](/mashery/cluster.jpg)
 > Un cluster d'esempio Mashery su piattaforma Kubernetes

Di seguito l'elenco dei container/componenti di Mashery:

- Traffic Manager (TM): il proxy che si occupa dell'autenticazione, elaborazione e instradamento delle chiamate. Di gran lunga il componente più importante poiché è quello che direttamente eroga il servizio verso i client.
- [Cassandra](http://cassandra.apache.org/) Registry: un database noSQL che tiene traccia della topologia dei componenti stessi e, in caso di installazione distribuita geograficamente, la condivide e sincronizza tra le diverse zone.
- [MySQL](https://www.mysql.com/) DB: persiste tutte le configurazioni e gli oggetti configurati dal CC o dalla Mashery API e necessari al funzionamento del gateway.
- Cache: basato su [Memcached](https://memcached.org/) si occupa del caching opzionale delle risposte ai servizi e di mantenere in cache le informazioni per le quali è richiesto un accesso veloce e ricorrente da parte dei TM (ad esempio le chiavi d'accesso).
- Log Service: basato su [Fluentd](https://www.fluentd.org/), si occupa dell'accentramento di tutti i log provenienti dagli altri componenti e dell'eventuale instradamento a piattaforme esterne di log management (elastic, splunk, ...).
- Cluster Manager (CM): espone l'API di prodotto e mette a disposizione una command line per operazioni amministrative a basso livello.

> Le considerazioni fatte in questa sezione valgono per un'installazione local di Mashery. Non esiste documentazione ufficiale sul funzionamento interno del Gateway in modalità cloud tuttavia possiamo presumere con una certa dose di sicurezza che non si discosti affatto da quanto scritto.
{.is-warning}


Il dominio di default del gateway cloud (vale a dire dei traffic manager messi a disposizione da Tibco) è [*\<nomeareacliente\>.api.mashery.com*](http://www.blankwebsite.com/). Analogamente al Dev Portal è possibile raggiungere il TM definendo un CNAME customizzabile in modo da "brandizzare" il dominio.

# Deployment
Mashery può essere deployato in tre diverse modalità: 
- [Cloud](#cloud)
- [Local Hybrid](#hybrid)
- [Local Untethered](#untethered)

> Tibco considera Mashery in modalità *Cloud* quasi come fosse un prodotto separato ([*Tibco Cloud Mashery*](https://docs.tibco.com/products/tibco-cloud-mashery)) categorizzandolo come uno dei tanti servizi messi a disposizione nella sua offerta cloud. Analogamente la modalità *Local* ([*Tibco Mashery Local*](https://docs.tibco.com/products/tibco-mashery-local-5-3-0)) ha documentazione e supporto dedicati. Ciò non toglie che sotto al cofano Mashery è un'unica piattaforma e un cliente può benissimo utilizzare il prodotto contemporaneamente in entrambe le modalità con la stessa sottoscrizione (a patto che abbia le opportune licenze).
{.is-info}


## Cloud
In modalità cloud tutti i componenti del gateway sono deployati sul cloud e la gestione della piattaforma è completamente delegata a Tibco. L'amministratore si occupa unicamente della configurazione del gateway e delle API.
Questa modalità ha come punto di forza l'assenza di overhead per la gestione ad parte del cliente, tuttavia occorre tenere presente che:

1. Occorrerà stabilire un canale di comunicazione sicuro e privato (VPN) e/o autenticare tutte le comunicazioni tra il cloud Tibco e i backend del cliente.
2. Il flusso dati transita su di un cloud in gestione a una società esterna, Tibco. Ci sono clienti (ad esempio banche o società appaltatrici dell'esercito) per cui la riservatezza e le limitazioni contrattuali sulla locazione geografica dei dati non consentono l'utilizzo di strumenti cloud.

## Local 
In modalità *Local* parte dei o tutti i componenti sono installati in locale e sono quindi sotto diretto controllo e gestione da parte del cliente.
> *Local* non significa necessariamente *on-premises*: un'installazione Mashery può benissimo risiedere su un'area cloud privata e viene comunque definita *Local* e non *Cloud*.
{.is-info}


#### Hybrid
In modalità ibrida, anche detta tethered (dall'inglese *tether*: "corda, collegamento") il componente Gateway viene installato e gestito dal cliente in locale. 
I restanti componenti (CC, Dev Portal, API di prodotto) continuano a essere in gestione a Tibco. Si rende necessaria una sincronizzazione costante tra la parte local e quella cloud (essenzialmente l'ambiente locale recepisce le configurazioni effettuate sul CC e l'ambiente cloud riceve aggiornamenti sulle statistiche d'uso delle API esposte). La comunicazione in entrambe le direzioni avviene unicamente tramite interrogazioni dal local a un servizio cloud dedicato (il MOM, *Mashery On-Prem Manager*).

#### Untethered
In modalità untethered tutti i componenti vengono installati e gestiti esclusivamente in locale. Ci sono alcune variazioni di nomenclatura (eg: il Control Center locale viene chiamato *Configuration Manager* mentre il Developer Portal per distinzione diventa *Local Developer Portal*) e alcune funzionalità disponibili sui portali cloud sono diverse e/o assenti. Non c'è comunicazione alcuna con il MOM.

> Le due modalità Hybrid e Untethered sono mutualmente esclusive e la scelta deve essere fatta in fase di installazione di Mashery Local.
{.is-warning}
