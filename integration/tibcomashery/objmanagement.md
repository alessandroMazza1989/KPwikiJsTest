---
title: Configurazione e gestione degli oggetti
description: 
published: true
date: 2020-05-26T12:15:09.931Z
tags: 
---

## Utilizzo dell'API Mashery

> ![tenor.gif](/mashery/tenor.gif)
> La API di prodotto Mashery è esposta a sua volta da un gateway Mashery. 
{.is-info}

Per invocare la API di Mashery è necessario accedere al sito developer.mashery.com e creare una [applicazione](/integration/tibcomashery/intro#applicazione) client.

> L'[utenza](/integration/tibcomashery/intro#utente) con la quale si accede al dev portal e si crea l'applicazione deve essere profilata con un [ruolo](/integration/tibcomashery/intro#ruolo) che abbia i necessari privilegi nell'[area](/integration/tibcomashery/intro#area) (o le aree) sulle quali si vuole andare ad agire tramite API. Per il dettaglio dei privilegi di ogni ruolo si faccia riferimento alla relativa [documentazione](http://docs.mashery.com/manage/GUID-BC63BAB0-7BFE-4F0E-887F-CF32342F8F9E.html).
{.is-info}

Una volta creata l'applicazione verranno staccati una [chiave](/integration/tibcomashery/intro#chiave) e un [secret](/integration/tibcomashery/intro#secret) da usare per autenticare le chiamate. La chiave sarà inizialmente in stato *waiting* fino all'approvazione da parte di Tibco.

> ![mashery_api_register.jpg](/mashery/mashery_api_register.jpg)
> *Schermata di riepilogo delle chiavi associate all'account*

> La chiave creata ha inizialmente un [throttle](/integration/tibcomashery/features#throttle) di 2 QPS e una [quota](/integration/tibcomashery/features#quota) di 5000 chiamate al giorno. Se si vogliono modificare questi limiti è necessario contattare Tibco.
{.is-info}

L'autenticazione è di tipo [oauth2](/integration/tibcomashery/features#oauth2) con grant type [*password*](https://www.oauth.com/oauth2-servers/access-tokens/password-grant/), richiede quindi che venga staccato un token d'accesso. Il token endpoint è *https://api.mashery.com/v3/token* e nella chiamata devono essere passati:
- chiave e secret come *username* e *password* della basic authentication
- UUID dell'area, nome utente e password dell'utenza Mashery all'interno di parametri url-encoded nel body (rispettivamente *scope*, *username*, *password*)

> ![mashery_api_token.jpg](/mashery/mashery_api_token.jpg)
> *Esempio di chiamata di fetch di un token per l'API di prodotto*

A questo punto le chiamate alle risorse andranno autenticate passando l'access token ricevuto come bearer token nell'header *authorization*.

> ![mashery_api_get_svcs.jpg](/mashery/mashery_api_get_svcs.jpg)
> *Esempio di chiamata di fetch dell'elenco dei servizi esposti*

L'elenco delle risorse interrogabili con i relativi URI si trova nella [documentazione ufficiale](https://developer.mashery.com/docs/read/mashery_api/30/resources).

> Di default nella response vengono passati solo alcuni degli attributi disponibili. Per ottenere più informazioni (o al contrario per limitare l'output e la dimensione della risposta) occorre specificare tramite il query parameter *values* i campi desiderati, ad esempio *https://api.mashery.com/v3/rest/members?fields=email,lastLogin* restituirà esclusivamente la mail di registrazione e la data di ultimo accesso di tutti gli utenti registrati all'area. La lista degli attributi specificabili è disponibile nella documentazione di ogni risorsa.
{.is-info}

> A causa delle limitazioni sulle utenze (un'utenza cloud non può autenticarsi alla API di prodotto e un'utenza local non può avere privilegi sull'intera area cliente) Tibco ha introdotto un'utenza tecnica, il ***service account***. 
> 
> Il service account:
> · è una speciale utenza cloud utilizzabile per autenticarsi alla API di prodotto con privilegi amministrativi su tutti gli oggetti dell'area cliente.
> · viene predisposto in fase di creazione dell'area stessa e associato alla mail dell'account owner (il manager a cui nome è stata effettuata la sottoscrizione al cloud Tibco).
> · viene solitamente creato con username *nomeareacliente_serviceaccount*
{.is-warning}

>[Qui](https://documenter.getpostman.com/view/4885521/RzfcKqGJ?version=latest) e [qui](/mashery/mashery_api.postman_collection.json) è reperibile una collection postman per effettuare chiamate alla API.
{.is-info}