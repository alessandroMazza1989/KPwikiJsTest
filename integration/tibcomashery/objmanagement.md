---
title: Configurazione e gestione degli oggetti
description: 
published: true
date: 2020-05-22T14:34:07.101Z
tags: 
---

### Utilizzo dell'API Mashery

Per invocare l'API di prodotto è necessario accedere al sito developer.mashery.com e creare una [applicazione](/integration/tibcomashery/intro#applicazione) client. L'[utenza](/integration/tibcomashery/intro#utente) con la quale si accede dovrà anche essere profilata con un [ruolo](/integration/tibcomashery/intro#ruolo) adatto sull'[area](/integration/tibcomashery/intro#area) (o le aree) sulle quali si vuole andare ad agire tramite API.
Una volta creata l'applicazione verranno staccati una [chiave](/integration/tibcomashery/intro#chiave) e un [secret](/integration/tibcomashery/intro#secret) da usare per autenticare le chiamate verso l'API. La chiave sarà inizialmente in stato *waiting* fino all'approvazione da parte di Tibco.
L'autenticazione è di tipo [oauth2](/integration/tibcomashery/features#oauth2) con grant type [*password*](https://www.oauth.com/oauth2-servers/access-tokens/password-grant/), dove chiave e secret andranno

>[Qui](https://documenter.getpostman.com/view/4885521/RzfcKqGJ?version=latest) e/o [qui](/mashery/mashery_api.postman_collection.json) è reperibile una collection postman per effettuare chiamate all'API.
{.is-info}