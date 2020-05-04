---
title: Funzionalità di prodotto
description: 
published: true
date: 2020-05-04T12:44:12.225Z
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
Una volta che il gateway è in grado di [identificare](#autenticazione-autorizzazione) con certezza il client associato ad ogni chiamata 
## Filtraggio delle chiamate
stabilire e far rispettare regole che stabiliscono quali client possono accedere ai servizi e quali no
## Throttling
## Notifiche di eventi
## Caching
## Processing delle chiamate
## Documentazione e divulgazione delle API
## Organizzazione gerarchica degli oggetti
## Amministrazione *self-service* degli oggetti