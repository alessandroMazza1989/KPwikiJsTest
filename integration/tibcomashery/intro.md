---
title: Introduzione e funzionalità di Mashery
description: 
published: true
date: 2020-04-27T13:01:03.724Z
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

## Area

Quando viene effettuata una sottoscrizione a Mashery Tibco crea una **area** dedicata al cliente. Tutti gli oggetti verranno creati all'interno di questa area.

![area.jpg](/mashery/area.jpg)

Ogni area ha UUID e ID univoci che la identificano e possono essere utili in caso di contatti con il supporto.

## Organizzazione

Una [**organizzazione**](http://docs.mashery.com/manage/GUID-EAD30F7B-689D-4BC5-9B25-28CD6BD400A7.html) è un contenitore di risorse (API, Pacchetti, Documentazione, ecc.) fra loro logicamente collegati. Ad esempio un'organizzazione può essere creata per raccogliere le risorse dedicate a una certa Business Unit del cliente oppure a un dato gruppo di lavoro. Tutte le organizzazioni sono figlie dell'area, che nella pratica è l'organizzazione *root* all'interno della quale risiedono tutte le altre.

![organizations.jpg](/mashery/organizations.jpg)

In ogni organizzazione è possibile definire sotto-organizzazioni che funzionano esattamente come le organizzazioni stesse. Ad esempio nell'organizzazione dedicata a un gruppo di lavoro si potrebbe creare una sotto-organizzazione dedicata a uno specifico progetto in sviluppo. Non è possibile scendere ulteriormente nell'albero, quindi il livello massimo è il 3 (non esistono "sotto-sotto-organizzazioni").

## Ruolo
I **ruoli** assegnati all'utente Mashery determinano quali oggetti esso può vedere e/o modificare sia nel CC che nel Dev Portal. 
Esistono diversi tipi di ruoli, come illustrato nei seguenti paragrafi.
#### Defaul Roles

#### Control Center Roles
Questi [ruoli](http://docs.mashery.com/manage/GUID-BC63BAB0-7BFE-4F0E-887F-CF32342F8F9E.html) riguardano esclusivamente il CC e possiamo definirli "Area Level" poiché regolano la visibilità a livello dell'intera area cliente. 
#### Organization Roles
Per ogni organizzazione creata Mashery genera automaticamente una serie di [ruoli](http://docs.mashery.com/manage/GUID-EAD30F7B-689D-4BC5-9B25-28CD6BD400A7.html), analoghi ai Control Center Role, con la differenza che in questo caso la visibilità è solo sulla determinata organizzazione.
#### Portal Access Groups
Come suggerito dal nome Tibco li considera "gruppi", non ruoli, tuttavia hanno la stessa funzione e le stesse caratteristiche ma in ambito Dev Portal. Determinano cioè la visibilità da parte dei developer degli oggetti a loro visibili ([piani](#piano) e [documentazione interattiva](#documentazione-interattiva)). Sono customizzabili: vengono creati con un nome a piacere tramite il CC ed è possibile definire liberamente quali utenti ne fanno parte e a quali risorse hanno accesso.

## API
Il primo oggetto da considerare è ovviamente l'**API** o **servizio**. Una API è essenzialmente un contentitore logico di endpoints. Vi sono alcune configurazioni che possono essere effettuate a livello di API ma in generale esse vengono sovrascritte dalle configurazioni impostate sul singolo endpoint.

![api_list.jpg](/mashery/api_list.jpg)

Il 99% dei servizi moderni appartiene a una delle due famiglie **REST** o **SOAP**. Mashery supporta entrambi gli standard con un livello variabile di successo. Non è fra gli obiettivi di questa guida illustrare le caratteristiche dei due paradigmi tuttavia una loro conoscenza di base è consigliata.

## Endpoint
L'**endpoint** è sicuramente l'oggetto più importante e più complesso di Mashery. Un endpoint rappresenta un canale di comunicazione tra il gateway e il mondo esterno. Ogni endpoint deve avere un indirizzo (URI, Uniform Resource Identifier) che lo identifica in maniera univoca e universale: non possono esistere due URI uguali sulla rete. Tramite un endpoint il client è in grado di accedere a una o più risorse messe a disposizione dal backend; per fare ciò il client invia richieste all'endpoint e riceve risposte dallo stesso.

![ep_list.jpg](/mashery/ep_list.jpg)

La maggioranza delle configurazioni necessarie alla pubblicazione di una API sul gateway viene effettuata a livello di singolo endpoint. Come già detto in Mashery gli endpoints sono raggruppati logicamente all'interno dei servizi.

> Esiste un certo livello di ambiguità tra gli addetti ai lavori su cosa sia un servizio. C'è chi identifica il servizio con il singolo endpoint e chi invece lo identifica con un gruppo di endpoints funzionalmente imparentati (vale a dire una API). Sia nella documentazione ufficiale Tibco che in questo documento quando si parla di servizio ci si riferisce *sempre* a una API.
{.is-info}

## Metodo

Un **metodo** è un'ulteriore suddivisione logica messa a disposizione dal gateway per distinguere operazioni/risorse diverse accessibili tramite lo stesso endpoint. In quest'ottica è anche possibile considerare un endpoint come un raggruppamento logico di metodi, completando quindi la gerarchia.

![api_hierarchy.jpg](/mashery/api_hierarchy.jpg)

La configurazione dei metodi è opzionale in Mashery e si adatta particolarmente bene all'archetipo SOAP, in cui il metodo è sovrapponibile al concetto di *SOAP operation*, mentre risulta superflua nei servizi REST (escludendo casi limite in cui il cliente necessita di alcune funzionalità specifiche implementabili esclusivamente tramite i metodi, che verranno trattate in seguito).

> Il metodo Mashery **non** corrisponde al metodo REST!
{.is-warning}


## Utente
Un oggetto **utente** viene creato indifferentemente al momento della registrazione sul Dev Portal (in *self-service*) o da un amministratore nel Control Center. L'utente è legato indissolubilmente a un indirizzo mail, tuttavia è concesso creare più utenti associati allo stesso indirizzo. Al momento della creazione in *self-service* verrà inviata una mail con un link di conferma prima di finalizzare la creazione.

![users.jpg](/mashery/users.jpg)

> Una particolarità degli utenti Mashery è che sono salvati in una tabella condivisa tra tutte le aree dei vari clienti. Ciò significa che il campo *Username* deve essere necessariamente univoco, in caso contrario la creazione fallirà.
{.is-info}

## Applicazione

## Pacchetto

## Piano

## Chiave

## Documentazione Interattiva

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