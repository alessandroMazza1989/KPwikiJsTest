---
title: Configurazione e gestione degli oggetti
description: 
published: true
date: 2020-05-22T15:24:06.661Z
tags: 
---

## Utilizzo dell'API Mashery

> L'API di prodotto di Mashery è esposta a sua volta da un gateway Mashery.
{.is-info}

Per invocare l'API di Mashery è necessario accedere al sito developer.mashery.com e creare una [applicazione](/integration/tibcomashery/intro#applicazione) client. L'[utenza](/integration/tibcomashery/intro#utente) con la quale si accede deve essere profilata con un [ruolo](/integration/tibcomashery/intro#ruolo) adatto sull'[area](/integration/tibcomashery/intro#area) (o le aree) sulle quali si vuole andare ad agire tramite API.
Una volta creata l'applicazione verranno staccati una [chiave](/integration/tibcomashery/intro#chiave) e un [secret](/integration/tibcomashery/intro#secret) da usare per autenticare le chiamate. La chiave sarà inizialmente in stato *waiting* fino all'approvazione da parte di Tibco.

> ![mashery_api_register.jpg](/mashery/mashery_api_register.jpg)
> *Schermata di riepilogo delle chiavi associate all'account*

> La chiave creata ha inizialmente un [throttle](/integration/tibcomashery/features#throttle) di 2 QPS e una [quota](/integration/tibcomashery/features#quota) di 5000 chiamate al giorno. Se si vogliono modificare questi limiti occorre contattare Tibco.
{.is-info}

L'autenticazione è di tipo [oauth2](/integration/tibcomashery/features#oauth2) con grant type [*password*](https://www.oauth.com/oauth2-servers/access-tokens/password-grant/), richiede quindi che venga staccato un token d'accesso. Il token endpoint è *https://api.mashery.com/v3/token* e nella chiamata devono essere passati:
- chiave e secret come *username* e *password* della basic authentication
- UUID dell'area, nome utente e password all'interno di parametri url-encoded nel body (rispettivamente *scope*, *username*, *password*)

> ![mashery_api_token.jpg](/mashery/mashery_api_token.jpg)
> *Esempio di chiamata di fetch di un token per l'API di prodotto*

A questo punto le chiamate alle risorse andranno autenticate passando l'access token ricevuto come bearer token nell'header *authorization*.

> ![mashery_api_get_svcs.jpg](/mashery/mashery_api_get_svcs.jpg)
> *Esempio di chiamata per recuperare l'elenco dei servizi esposti*

> Di default nella response vengono passati solo alcuni degli attributi disponibili. Per ottenere più informazioni (o al contrario per limitare l'output e la dimensione della risposta) occorre specificare nel query tramite il query parameter *values* i campi desiderati, ad esempio *https://api.mashery.com/v3/rest/members?fields=email,lastLogin* restituirà esclusivamente la mail di registrazione e la data di ultimo accesso di tutti gli utenti registrati all'area. L'elenco degli attributi specificabili è disponibile nella [documentazione](https://developer.mashery.com/docs/read/mashery_api/30/resources) di ogni risorsa.
{.is-info}

TODO: **SERVICEACCOUNT** (qui e nella sezione utente)

>[Qui](https://documenter.getpostman.com/view/4885521/RzfcKqGJ?version=latest) e/o [qui](/mashery/mashery_api.postman_collection.json) è reperibile una collection postman per effettuare chiamate all'API.
{.is-info}