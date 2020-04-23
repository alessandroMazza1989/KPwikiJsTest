---
title: Introduzione e funzionalità di Mashery
description: 
published: true
date: 2020-04-23T15:30:44.781Z
tags: mashery, api, tibco, api gateway
---

# Cosa è un API Gateway
Un API Gateway si occupa di fare da proxy tra i client che vogliono accedere alle risorse messe a disposizione dalle varie API e i sistemi di backend dove i servizi sono in esecuzione. Ciò significa che la funzione primaria del gateway è ricevere una chiamata da un client, smistarla verso il corretto backend di destinazione, ricevere la risposta e restituirla al client stesso.

![api_gateway.jpg](/mashery/api_gateway.jpg){.align-center}

Ovviamente questa è una visione semplicistica: lo strumento mette a disposizione una serie di features aggiuntive che verranno illustrate nei paragrafi seguenti.

# Oggetti
L'organizzazione logica interna di Mashery si basa su una serie di oggetti. Semplificando questi oggetti possono essere visti come record di tabelle di un database. Ogni oggetto ha degli attributi configurabili ed è collegato gerarchicamente ad altri oggetti.

![objects.jpg](/mashery/objects.jpg)

Nei paragrafi seguenti verranno illustrati gli oggetti più importanti.

## API
Il primo oggetto da considerare è ovviamente l'**API** o **servizio**. Una API è essenzialmente un contentitore logico di endpoints. Vi sono alcune configurazioni che possono essere effettuate a livello di API ma in generale esse vengono sovrascritte dalle configurazioni impostate sul singolo endpoint.

![api_list.jpg](/mashery/api_list.jpg)

Il 99% dei servizi moderni appartiene a una delle due famiglie **REST** o **SOAP**. Mashery supporta entrambi gli standard con un livello variabile di successo. Non è fra gli obiettivi di questa guida illustrare le caratteristiche dei due paradigmi tuttavia una loro conoscenza di base è consigliata.

## Endpoint
L'**endpoint** è sicuramente l'oggetto più importante e più complesso di Mashery. Un endpoint rappresenta un canale di comunicazione tra il gateway e il mondo esterno. Ogni endpoint deve avere un indirizzo (URI, Uniform Resource Identifier) che lo identifica in maniera univoca e universale: non possono esistere due URI uguali sulla rete. Tramite un endpoint il client è in grado di accedere a una o più risorse messe a disposizione dal backend; per fare ciò il client invia richieste all'endpoint e riceve risposte dallo stesso.

![ep_list.jpg](/mashery/ep_list.jpg)

La maggioranza delle configurazioni necessarie alla pubblicazione di una API sul gateway viene effettuata a livello di singolo endpoint. Come già detto in Mashery gli endpoints sono raggruppati logicamente all'interno dei servizi.

**NB**: esiste un certo livello di ambiguità tra gli addetti ai lavori su cosa sia un servizio. C'è chi identifica il servizio con il singolo endpoint e chi invece lo identifica con un gruppo di endpoints funzionalmente imparentati (vale a dire una API). Sia nella documentazione ufficiale Tibco che in questo documento quando si parla di servizio ci si riferisce *sempre* a una API.

## Metodo

## Utente

## Ruolo

## Applicazione

## Pacchetto

## Piano

## Chiave

# Funzionalità
Di seguito la lista delle macro funzionalità che Tibco Mashery mette a disposizione di un cliente per gestire la sua API governance:

1. Autenticazione & Autorizzazione
2. Auditing
3. Filtraggio delle chiamate
4. Throttling
5. Notifiche di eventi
5. Caching
6. Processing delle chiamate
7. Documentazione e divulgazione delle API
8. Organizzazione gerarchica degli oggetti
9. Amministrazione *self-service* degli oggetti