---
title: Funzionalità di prodotto
description: 
published: true
date: 2020-05-04T13:44:49.740Z
tags: mashery, tibco, api gateway
---

Nelle sezioni successive sono dettagliate le macro funzionalità che Tibco Mashery mette a disposizione di un cliente per implementare la sua API governance.

## Autenticazione & Autorizzazione
Una delle funzionalità più importanti, se non la più importante, che il gateway fornisce è l'abilità di accertare l'identità dei chiamanti (**autenticazione**) e stabilire di conseguenza a quali risorse essi abbiano eventualmente accesso (**autorizzazione**). Per fare ciò Mashery mette a disposizione diversi metodi.

> In Mashery l'autenticazione deve essere impostata su ogni singolo [endpoint](/integration/tibcomashery/intro#endpoint), non è possibile agire sull'intera [API](/integration/tibcomashery/intro#api).
{.is-info}

> In Mashery deve **sempre** essere impostata un'autenticazione su ogni endpoint, perché il gateway deve necessariamente essere in grado di identificare il chiamante. La possibilità di avere endpoint non autenticati esiste ma va realizzata tramite un tipico [*Tibco Beardtrick*](#INSERIRELINK) alquanto posticcio (è stato evidentemente aggiunto in corsa su richiesta dei clienti).
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
Per fare ciò Mashery produce *access logs* interni che possono essere consultati direttamente e/o rediretti verso piattaforme di log management (elastic, splunk, ...).

### Access Logs
Gli access log a più basso livello prodotti dai *traffic manager* e raccolti nei *log service* pods (cfr [architettura del gateway]((/integration/tibcomashery/architecture#gateway))
>`dev-api.pirelli.com 217.244.212.244,217.244.212.244 9383c97f-1bfd-4f71-a87e-f73dbf8a355f cors_actual [04/May/2020:13:07:31 +0000] "POST /buynow/products/availability?targetCountry=DE HTTP/1.1" 2 200 "https://www.pirelli.com/tyres/de-de/pkw/produkte" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.129 Safari/537.36" 1588597651.531_6szb9htdxqsqzgu9vtz7b8d3_fv3b8qx4gabtp9zkfpvp37sy "-" "tm-deploy-0-7f88c87bd5-z7mg4" "-" 0 - 0.388 0.085 0.017 0.000 - - - - - 0 99556 100 0 99556 100 0 0 0 99556 286270 0 0 0 0 0 0.000`
> *Esempio di entry dell'access log di Mashery*



### Enriched Access Logs
Gli [enriched access logs](https://docs.tibco.com/pub/mash-local/5.3.0/doc/html/GUID-267B417C-2D51-4C13-820B-C862EC7BCAF6.html)
>`6szb9htdxqsqzgu9vtz7b8d3,-,2,0,0.0,0.017,dev_ep_buynow.products.availability,POST,200,HTTP/1.1,-,b2cws,50ebc3cd-8bbd-44cd-8eee-8db2c2cab794,b2cws_dev,6a48b6c5-ba9c-44bb-9a74-6f63f3580360,0.0,0,0,https://www.pirelli.com/tyres/de-de/pkw/produkte,0.085,dev-api.pirelli.com,1588597651.531_6szb9htdxqsqzgu9vtz7b8d3_fv3b8qx4gabtp9zkfpvp37sy,2020-05-04T13:07:31,9383c97f-1bfd-4f71-a87e-f73dbf8a355f,200 OK (API),p84es3f7b6k7zv85gavnb9cb,fv3b8qx4gabtp9zkfpvp37sy,api_buynow,217.244.212.244,217.244.212.244,0,0.388,tm-deploy-0-7f88c87bd5-z7mg4,-,/buynow/products/availability?targetCountry=DE,Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.129 Safari/537.36`
> *La stessa chiamata del precedente esempio in formato enriched access log*

## Filtraggio delle chiamate
stabilire e far rispettare regole che stabiliscono quali client possono accedere ai servizi e quali no
## Throttling
## Notifiche di eventi
## Caching
## Processing delle chiamate
## Documentazione e divulgazione delle API
## Organizzazione gerarchica degli oggetti
## Amministrazione *self-service* degli oggetti