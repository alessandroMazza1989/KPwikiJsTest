---
title: Funzionalità di prodotto
description: 
published: true
date: 2020-05-15T12:24:36.881Z
tags: mashery, tibco, api gateway
---

Nelle sezioni successive sono dettagliate le macro funzionalità che Tibco Mashery mette a disposizione di un cliente per implementare la sua API governance.

## Autenticazione & Autorizzazione
Una delle funzionalità più importanti, se non la più importante, che il gateway fornisce è l'abilità di accertare l'identità dei chiamanti (**autenticazione**) e stabilire di conseguenza a quali risorse essi abbiano eventualmente accesso (**autorizzazione**). Per fare ciò Mashery mette a disposizione diversi metodi.

> In Mashery l'autenticazione deve essere impostata su ogni singolo [endpoint](/integration/tibcomashery/intro#endpoint), non è possibile agire sull'intera [API](/integration/tibcomashery/intro#api).
{.is-info}

> In Mashery deve **sempre** essere impostata un'autenticazione su ogni endpoint, perché il gateway deve necessariamente essere in grado di identificare il chiamante. La possibilità di avere endpoint non autenticati (*noauth*) esiste ma va realizzata tramite un tipico [*Tibco Beardtrick*](#INSERIRELINK) alquanto posticcio (è stato evidentemente aggiunto in corsa su richiesta dei clienti).
{.is-warning}

### API Key
Nell'autenticazione tramite **API key** il client deve includere la sua chiave in ogni chiamata. La chiave deve essere sicura e conosciuta solo dal gateway e dal client stesso. Mashery si occupa di generare le [chiavi](/integration/tibcomashery/intro#chiave) e quindi di verificarne puntualmente la validità.

>![api_key_config.jpg](/mashery/api_key_config.jpg)
> *Esempio di endpoint configurato per autenticazione tramite API key*

Se il gateway non rileva nella richiesta una chiave valida l'accesso alla risorsa viene negato e una risposta di errore restituita al client. In questo caso non viene effettuata nessuna chiamata verso il backend.

>![403_error.jpg](/mashery/403_error.jpg)
> *Esempi di risposta d'errore restituita dal gateway in caso di autenticazione negata (chiave assente/invalida) o di autorizzazione negata (chiave corretta ma non valida per lo specifico endpoint)*

### OAuth2
Il protocollo [**OAuth2**](https://tools.ietf.org/html/rfc6749) prevede che in ogni chiamata sia incluso un *token* di accesso. Il conseguente meccanismo di autenticazione e autorizzazione da parte del gateway è analogo a quello già visto per la [API key](#api-key): in caso di token mancante o invalido non è consentito accesso alla risorsa invocata e viene restituito un messaggio di errore.

>![401_mashery_api.jpg](/mashery/401_mashery_api.jpg)
> *Esempio di risposta d'errore restituita dalla API di prodotto (esposta da un gateway Mashery) in caso di token errato o scaduto*

La maggiore sicurezza garantita da questo protocollo deriva dal fatto che il token sia temporaneo e che debba essere staccato o rinnovato frequentemente da ogni client. Vi sono diversi modi ([*Grant Types*](https://oauth.net/2/grant-types/)) per il client di richiedere e ricevere un token ma tutti quanti prevedono la presenza di un *token endpoint* preposto al provisioning e al refreshing dei token.

>![token_ep.jpg](/mashery/token_ep.jpg)
> *Esempio di invocazione riuscita ad un token endpoint; come si può vedere nella risposta è esplicitata anche la durata del token stesso*

## Auditing
Una volta che il gateway è in grado di [identificare](#autenticazione-autorizzazione) con certezza il client associato ad ogni chiamata il logico step successivo è mantenere un registro delle richieste con il maggior numero di informazioni possibili, tra cui ovviamente chi ha invocato quale endpoint e in quale momento.
Per fare ciò Mashery produce [*access logs*](/integration/tibcomashery/mladministration#access-logs) interni che possono essere consultati direttamente (principalmente per finalità di debugging) e/o rediretti verso piattaforme di log management di terze parti in modo da essere categorizzati, trasformati e resi più fruibili ai fini statistici.

### Executive Summary
L'[Executive Summary](http://docs.mashery.com/analyze/GUID-C4E657F4-34A7-4788-B08B-F6738C7A3CB8.html) è una sezione del [Control Center](/integration/tibcomashery/architecture#control-center) che consente una visione ad altissimo livello di alcune statistiche d'uso relative all'[area](/integration/tibcomashery/intro#area). E' ben documentato e non c'è molto da aggiungere qui se non che i tempi di caricamento delle singole view sono molto lunghi, soprattutto selezionando archi temporali ampi.

> ![executive_summary.jpg](/mashery/executive_summary.jpg)
> *Executive summary per l'area pirelliapiportal*

### Reports
La sezione dedicata ai [Reports](http://docs.mashery.com/analyze/GUID-98A019E2-0870-4D34-B23E-39B41A535114.html) nel [Control Center](/integration/tibcomashery/architecture#control-center) presenta una serie di dashboard dalle quali è possibile estrapolare informazioni d'uso più capillari con focus sui singoli [package](/integration/tibcomashery/intro#pacchetto) o sui singoli [servizi](/integration/tibcomashery/intro#api).

![reports.jpg](/mashery/reports.jpg)

I principali svantaggi di questa dashboard fornita out-of-the-box sono la lentezza di caricamento delle singole view e l'impossibilità di esportare i dati integralmente (è solo possibile scaricare i dati di ogni singola view). Inoltre la GUI è decisamente spartana e non è dato customizzare la dashboard in alcun modo: si è limitati a quello che Tibco mette a disposizione.

### Piattaforme di Log Management
Mashery fornisce nativamente la possibilità di instradare puntualmente i log di prodotto a piattaforme di log management (elastic, splunk, kafka, ...) sia in un deployment [Cloud](/integration/tibcomashery/architecture#cloud) che [Local](/integration/tibcomashery/architecture#local).

Nel caso di un gateway cloud (tecnicamente anche local, ma solo in modalità hybrid/tethered) ciò è implementabile in maniera sincrona tramite la funzionalità di [Call Log Streams](http://docs.mashery.com/analyze/GUID-A085F6A2-AE7A-4D8F-9CA7-63D0DEBE2512.html) che trasmette puntualmente ogni log ad un endpoint di ingestion per mezzo di un WebSocket. Sono tuttavia possibili ritardi anche di svariati minuti tra una chiamata e la trasmissione del corrispondente log in formato JSON.

>![wss_logs.jpg](/mashery/wss_logs.jpg)
> *Esempio di log stream catturato tramite un WebSocket client di test*

Nel caso invece di un deployment local, sia untethered che hybrid, è il componente Log Service che si occupa dell'instradamento dei log verso una piattaforma esterna, purché vengano effettuate le necessarie [configurazioni](https://docs.tibco.com/pub/mash-local/latest/doc/html/GUID-7FE86E9D-943C-427C-98AA-C11B37BABBCF.html). Anche in questo caso i log vengono trasmessi in formato JSON, tuttavia il ritardo di trasmissione è di pochi secondi.

>![elastic_log.jpg](/mashery/elastic_log.jpg)
> *Esempio di document elastic derivato da un singolo log Mashery*

> Sia utilizzando la funzionalità di Call Log Streams che configurando Mashery Local per instradare i log ad oggi non è possibile in alcun modo modificare la struttura dei log stessi (aggiungere/rimuovere campi, ad esempio).
{.is-info}

## Filtro delle chiamate
Uno schermo di sicurezza aggiuntivo, che a onor del vero Mashery non fornisce out-of-the-box ma solamente tramite l'utilizzo di adapters, prevede la possibilità di permettere o negare l'accesso ai servizi implementando logiche di business. Questo filtro può essere in aggiunta all'[autenticazione](#autenticazione-autorizzazione) oppure stand-alone (in questo caso gli endpoint tecnicamente saranno non autenticati, cioè in [*noauth*](#inserire-link)).

Ad esempio è possibile permettere accesso solo a determinati IP ([IP Whitelisting Connector](http://docs.mashery.com/connectorsguide/GUID-1BEA3681-0C40-4398-8FED-1CB4F4A52942.html)) oppure al contrario negare accesso agli IP indesiderati ([IP Blocking Connector](http://docs.mashery.com/connectorsguide/GUID-3290F176-44C5-4D95-9DA1-4141B85B7FB7.html)). Alcuni adapter consentono anche di implementare filtri basati sulla chiamata stessa, ad esempio il [Whitelisting Connector](http://docs.mashery.com/connectorsguide/GUID-F3B0C216-9D0B-4BE1-A6A1-C789FD7576CA.html) e il [Block API Connector](http://docs.mashery.com/connectorsguide/GUID-74511B0B-CFB7-42AA-BAA8-C66F10E06151.html).

La stragrande maggioranza dei connettori forniti da Tibco può essere configurata esclusivamente tramite campi

## Throttling
## Notifiche di eventi
## Caching
## Processing delle chiamate
## Documentazione e divulgazione delle API
## Organizzazione gerarchica degli oggetti
## Amministrazione *self-service* degli oggetti