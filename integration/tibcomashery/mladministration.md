---
title: Amministrazione
description: 
published: true
date: 2020-05-07T13:51:14.536Z
tags: 
---

WIP

### Access Logs
Gli access log a più basso livello prodotti dai *traffic manager* e raccolti dal *log service* (cfr [architettura del gateway](/integration/tibcomashery/architecture#gateway)). Sono composti da *space separated values* e risultano abbastanza illeggibili ad un occhio non allenato.
>`dev-api.pirelli.com 217.244.212.244,217.244.212.244 9383c97f-1bfd-4f71-a87e-f73dbf8a355f cors_actual [04/May/2020:13:07:31 +0000] "POST /buynow/products/availability?targetCountry=DE HTTP/1.1" 2 200 "https://www.pirelli.com/tyres/de-de/pkw/produkte" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.129 Safari/537.36" 1588597651.531_6szb9htdxqsqzgu9vtz7b8d3_fv3b8qx4gabtp9zkfpvp37sy "-" "tm-deploy-0-7f88c87bd5-z7mg4" "-" 0 - 0.388 0.085 0.017 0.000 - - - - - 0 99556 100 0 99556 100 0 0 0 99556 286270 0 0 0 0 0 0.000`
> *Esempio di entry dell'access log di Mashery*

> Una lista dei campi e del loro significato è disponibile [qui](/mashery/mashery_accessloginterfacespecification.pdf).
{.is-info}

### Enriched Access Logs
Gli [enriched access logs](https://docs.tibco.com/pub/mash-local/latest/doc/html/GUID-267B417C-2D51-4C13-820B-C862EC7BCAF6.html) sono prodotti dal *log service* e, come suggerisce il nome, sono arricchiti di ulteriori informazioni rispetto agli access logs. In questo caso siamo passati a *comma separated values* ma la leggibilità è sempre mediocre.
>`6szb9htdxqsqzgu9vtz7b8d3,-,2,0,0.0,0.017,dev_ep_buynow.products.availability,POST,200,HTTP/1.1,-,b2cws,50ebc3cd-8bbd-44cd-8eee-8db2c2cab794,b2cws_dev,6a48b6c5-ba9c-44bb-9a74-6f63f3580360,0.0,0,0,https://www.pirelli.com/tyres/de-de/pkw/produkte,0.085,dev-api.pirelli.com,1588597651.531_6szb9htdxqsqzgu9vtz7b8d3_fv3b8qx4gabtp9zkfpvp37sy,2020-05-04T13:07:31,9383c97f-1bfd-4f71-a87e-f73dbf8a355f,200 OK (API),p84es3f7b6k7zv85gavnb9cb,fv3b8qx4gabtp9zkfpvp37sy,api_buynow,217.244.212.244,217.244.212.244,0,0.388,tm-deploy-0-7f88c87bd5-z7mg4,-,/buynow/products/availability?targetCountry=DE,Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.129 Safari/537.36`
> *La stessa chiamata del precedente esempio in formato enriched access log*

### Call Inspector
Il [call inspector](http://docs.mashery.com/analyze/GUID-402C28D5-283F-4AFD-9436-F0550A685F0A.html) è un tool di analisi e debug **esclusivamente** delle chiamate effettuate verso i TM cloud. Il suo scopo è principalmente sopperire all'impossibilità di accesso agli access log della parte cloud di Mashery.

>![call_inspector.jpg](/mashery/call_inspector.jpg)
> *Esempio di output del call inspector*

L'utilizzo dello strumento è decisamente macchinoso e richiede alcuni minuti prima che i log delle chiamate siano disponibili.