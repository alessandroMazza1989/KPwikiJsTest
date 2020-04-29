---
title: Funzionalità di prodotto
description: 
published: true
date: 2020-04-29T15:41:28.378Z
tags: mashery, tibco, api gateway
---

# Funzionalità
Nelle sezioni successive sono dettagliate le macro funzionalità che Tibco Mashery mette a disposizione di un cliente per gestire la sua API governance.

## Autenticazione & Autorizzazione
Una delle funzionalità più importanti, se non la più importante, che il gateway fornisce è l'abilità di accertare l'identità dei chiamanti (**autenticazione**) e stabilire di conseguenza a quali risorse essi abbiano eventualmente accesso (**autorizzazione**). Per fare ciò Mashery mette a disposizione diversi metodi.

> In Mashery l'autenticazione deve essere impostata su ogni singolo [endpoint](/integration/tibcomashery/intro#endpoint), non è possibile agire sull'intera [API](/integration/tibcomashery/intro#api).
{.is-info}

> In Mashery deve **sempre** essere impostata un'autenticazione su ogni endpoint, perché il gateway deve necessariamente essere in grado di identificare il chiamante. La possibilità di avere endpoint non autenticati esiste ma va implementata tramite un tipico [*Tibco Beardtrick*](#INSERIRELINK) alquanto posticcio (è stato evidentemente aggiunto in corsa su richiesta dei clienti).
{.is-warning}


### API Key
Nell'autenticazione tramite **API key** il client deve includere la sua chiave in ogni chiamata. La chiave deve essere sicura e conosciuta solo dal gateway e dal client stesso. Mashery si occupa di generare le [chiavi](/integration/tibcomashery/intro#chiave) e quindi di verificarne puntualmente la validità.

>![api_key_config.jpg](/mashery/api_key_config.jpg)
> *Esempio di endpoint configurato per autenticazione tramite API key*


## Auditing
## Filtraggio delle chiamate+
stabilire e far rispettare regole che stabiliscono quali client possono accedere ai servizi e quali no
## Throttling
## Notifiche di eventi
## Caching
## Processing delle chiamate
## Documentazione e divulgazione delle API
## Organizzazione gerarchica degli oggetti
## Amministrazione *self-service* degli oggetti