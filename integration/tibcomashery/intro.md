---
title: Introduzione e funzionalità di Mashery
description: 
published: true
date: 2020-04-29T14:27:14.712Z
tags: mashery, api, tibco, api gateway
---

# Cosa è un API Gateway
Un API Gateway si occupa di fare da proxy tra i client che vogliono accedere alle risorse messe a disposizione dalle varie API e i sistemi di backend dove i servizi sono in esecuzione. Ciò significa che la funzione primaria del gateway è ricevere una chiamata da un client, smistarla verso il corretto backend di destinazione, ricevere la risposta e restituirla al client stesso.

>![api_gateway.jpg](/mashery/api_gateway.jpg){.align-center}
> *Schema di base del funzionamento di un API gateway*

Ovviamente questa è una visione semplicistica: lo strumento mette a disposizione una serie di features aggiuntive che verranno illustrate più avanti.

# Oggetti
L'organizzazione logica interna di Mashery si basa su una serie di oggetti. Semplificando questi oggetti possono essere visti come record di tabelle di un database. Ogni oggetto ha degli attributi configurabili ed è collegato gerarchicamente ad altri oggetti.

>![objects.jpg](/mashery/objects.jpg)
> *Alcuni degli oggetti di Mashery con le rispettive relazioni*

Nei paragrafi seguenti verranno illustrati gli oggetti più importanti.

## Area

Quando viene effettuata una sottoscrizione a Mashery Tibco crea una **area** dedicata al cliente. Tutti gli oggetti verranno creati all'interno di questa area.

>![area.jpg](/mashery/area.jpg)
> *Dettaglio delle informazioni dell'area *pirelliapiportal**

Ogni area ha UUID e ID univoci che la identificano e possono essere utili in caso di contatti con il supporto.

## Organizzazione

Un'[**organizzazione**](http://docs.mashery.com/manage/GUID-EAD30F7B-689D-4BC5-9B25-28CD6BD400A7.html) è un contenitore di risorse (API, Pacchetti, Documentazione, ecc.) fra loro logicamente collegati. Ad esempio un'organizzazione può essere creata per raccogliere le risorse dedicate a una certa Business Unit del cliente oppure a un dato gruppo di lavoro. Tutte le organizzazioni sono figlie dell'area, l'organizzazione *root* all'interno della quale risiedono tutte le altre.

>![organizations.jpg](/mashery/organizations.jpg)
> *Esempio di struttura delle organizzazioni Mashery per un'ipotetica società*

In ogni organizzazione è possibile definire sotto-organizzazioni che funzionano esattamente come le organizzazioni stesse. Ad esempio nell'organizzazione dedicata a un gruppo di lavoro si potrebbe creare una sotto-organizzazione dedicata a uno specifico progetto in sviluppo. Non è possibile scendere ulteriormente nell'albero, quindi il livello massimo è il 3 (non esistono "sotto-sotto-organizzazioni").

## Ruolo
I **ruoli** assegnati all'utente Mashery determinano quali oggetti esso può vedere e/o modificare sia nel [Control Center](/integration/tibcomashery/architecture#control-center) che nel [Dev Portal](/integration/tibcomashery/architecture#developer-portal).

#### Control Center Roles
Questi [ruoli](http://docs.mashery.com/manage/GUID-BC63BAB0-7BFE-4F0E-887F-CF32342F8F9E.html) riguardano esclusivamente il CC e possono essere definiti "Area Level" poiché regolano la visibilità a livello dell'intera area cliente. (https://docs.mashery.com/manage/GUID-C3515849-9ADF-4673-9D02-EC3E54A22134.html).
> I Control Center Roles non possono essere assegnati dal CC stesso, si assegnano dal cloud Tibco.
{.is-warning}

>![area_roles.jpg](/mashery/area_roles.jpg)
> *Schermata di assegnazione dei Control Center Roles*

#### Organization Roles
Per ogni organizzazione creata Mashery genera automaticamente una serie di [ruoli](http://docs.mashery.com/manage/GUID-EAD30F7B-689D-4BC5-9B25-28CD6BD400A7.html), analoghi ai precedenti, con la differenza che in questo caso la visibilità sul CC è limitata ad una determinata organizzazione.

>![org_roles.jpg](/mashery/org_roles.jpg)
> *Schermata di assegnazione degli Organization Roles per un utente*

#### Portal Access Groups
Come suggerito dal nome Tibco li considera "gruppi", non ruoli, tuttavia hanno la stessa funzione e le stesse caratteristiche. Determinano la visibilità da parte dei developer degli unici oggetti da loro fruibili sul [Developer Portal](/integration/tibcomashery/architecture#developer-portal), cioè [piani](#piano) e [documentazione interattiva](#documentazione-interattiva). Sono customizzabili: vengono creati con un nome a piacere tramite il CC ed è possibile definire liberamente quali utenti ne fanno parte e a quali risorse hanno accesso.

>![access_groups.jpg](/mashery/access_groups.jpg)
> *Dettaglio di un gruppo d'accesso e delle risorse correlate*

> I seguenti ruoli sono utilizzabili, pur non essendo citati da nessuna parte nella documentazione ufficiale:
>
> *Everyone*: qualunque utente acceda al Dev Portal, sia quelli che hanno effettuato il log-in che quelli non autenticati.
> *Member*: un utente registrato che ha effettuato il log-in sul Dev Portal.
> *Organization User*: qualunque utente registrato che fa parte di almeno una [organizzazione](#organizzazione).
> *Service User*: il primo utente creato nell'area cliente. Si tratta di un ruolo tecnico assegnato da Tibco, inutile in ambito di amministrazione del gateway.
{.is-info}

## API
Una **API** o **servizio** è essenzialmente un contentitore logico di [endpoints](#endpoint). Vi sono alcune configurazioni che possono essere effettuate a livello di API ma in generale esse vengono sovrascritte da quelle del singolo endpoint.

>![api_list.jpg](/mashery/api_list.jpg)
> *Schermata di elenco delle API*

> Il 99% delle API moderne appartiene a una delle due famiglie **REST** o **SOAP**. Mashery supporta entrambi gli standard con un livello variabile di successo. Non è fra gli obiettivi di questa guida illustrare le caratteristiche dei due paradigmi tuttavia una conoscenza di base delle loro caratteristiche è consigliata.
{.is-info}


## Endpoint
L'**endpoint** è sicuramente l'oggetto più importante e più complesso di Mashery. Un endpoint rappresenta un canale di comunicazione tra il gateway e il mondo esterno. Ogni endpoint deve avere un indirizzo (URI, Uniform Resource Identifier) che lo identifica in maniera univoca e universale: non possono esistere due endpoint aventi lo stesso URI sulla rete. Tramite l'endpoint il client è in grado di accedere a una o più risorse messe a disposizione dal backend; per fare ciò il client invia richieste e riceve risposte dall'endpoint.

La maggioranza delle configurazioni necessarie alla pubblicazione di una API sul gateway viene effettuata a livello di singolo endpoint. Come già detto in Mashery gli endpoints sono raggruppati logicamente all'interno delle [API](#api).

>![ep_list.jpg](/mashery/ep_list.jpg)
> *Schermata di elenco degli endpoint di una API*

> Esiste un certo livello di ambiguità tra gli addetti ai lavori su cosa sia un servizio. C'è chi identifica il servizio con il singolo endpoint e chi invece lo identifica con un gruppo di endpoints funzionalmente imparentati (vale a dire una API). Sia nella documentazione ufficiale Tibco che in questo documento quando si parla di servizio ci si riferisce *sempre* a una API.
{.is-info}

## Metodo
Un [**metodo**](http://docs.mashery.com/design/GUID-AD59176F-2EAD-4214-B95E-CE98E3CC33DE.html) è un'ulteriore suddivisione logica messa a disposizione dal gateway per distinguere operazioni/risorse diverse accessibili tramite lo stesso [endpoint](#endpoint). In quest'ottica è anche possibile considerare un endpoint come un raggruppamento logico di metodi, completando quindi la gerarchia.

>![api_hierarchy.jpg](/mashery/api_hierarchy.jpg)
> *Gerarchia degli oggetti in Mashery*

L'utilizzo dei metodi è opzionale in Mashery e si adatta particolarmente bene all'archetipo SOAP, dove il metodo è sovrapponibile al concetto di *SOAP operation*, mentre risulta superflua nei servizi REST (escludendo casi limite in cui il cliente necessita di alcune funzionalità specifiche implementabili esclusivamente tramite i metodi).

> Il metodo Mashery **non** corrisponde al metodo REST!
{.is-warning}

## Utente
Un oggetto [**utente**](http://docs.mashery.com/manage/GUID-7D08A6AC-E20B-43A5-B5E2-B3E5551087C6.html) viene creato al momento della registrazione di un nuovo membro sul [Dev Portal](/integration/tibcomashery/architecture#developer-portal) o manualmente da un amministratore nel [Control Center](/integration/tibcomashery/architecture#control-center). L'utente è legato indissolubilmente a un indirizzo mail, tuttavia è concesso creare più utenti associati allo stesso indirizzo. Dopo la registrazione, se effettuata in *self-service*, verrà inviata una mail con un link di conferma prima di finalizzare la creazione.

>![users.jpg](/mashery/users.jpg)
> *Schermata di elenco degli utenti appartenenti all'[area](#area)*

> Una particolarità degli utenti Mashery è che sono salvati in uno spazio condiviso tra le aree dei vari clienti. Ciò significa che il campo *Username* deve essere necessariamente univoco sull'intero ambito del cloud Tibco, in caso contrario la creazione fallirà.
{.is-info}

## Applicazione
Un'[**applicazione**](http://docs.mashery.com/manage/GUID-8598F4C2-41F6-4703-A48B-545917EF8835.html) è l'oggetto che in Mashery rappresenta un client (quindi un'app, un frontend, un qualsiasi sistema in grado di effettuare chiamate) che può fruire dei servizi messi a disposizione dal gateway. L'applicazione deve essere associata ad uno e un solo utente, tuttavia un utente può creare più applicazioni.
> Non è possibile invocare gli endpoint esposti dal gateway senza prima aver creato un'applicazione, selezionato un [piano](#piano) di utilizzo e ricevuto una [chiave](#chiave) con cui identificare le proprie chiamate.
{.is-info}

>![applications.jpg](/mashery/applications.jpg)
> *Schermata di elenco delle applicazioni*

## Pacchetto
Il [**pacchetto**](http://docs.mashery.com/design/GUID-B9F7E9DA-6E0C-4300-9A1D-CB7B407BC5D3.html) è un raggruppamento logico di [piani](#piano) di utilizzo delle API. 

>![packages_plans.jpg](/mashery/packages_plans.jpg)
> *Esempio di pacchetto contenente tre diversi piani di accesso*

> Alcune (poche) configurazioni si effettuano a livello di pacchetto ma a tutti gli effetti si tratta semplicemente di un contenitore.
{.is-info}

>![packages.jpg](/mashery/packages.jpg)
> *Schermata di elenco dei pacchetti creati per l'[area](#area)*

## Piano
Un [**piano**](http://docs.mashery.com/design/GUID-B78424FD-C04D-4BBD-ACCA-73E0F6F90214.html) non può esistere se prima non è stato creato un [pacchetto](#pacchetto) che lo contenga.

>![plans.jpg](/mashery/plans.jpg)
> *Schermata di elenco dei piani appartenenti al pacchetto b2cws*

Nel piano è definita una lista di [API](#api)/[endpoints](#endpoint)/[metodi](#metodo) (la granularità è configurabile a piacere) a cui il piano stesso dà diritto di accesso. Oltre a ciò a questo livello possono essere definiti i limiti di [throttling](#throttling) e alcune proprietà delle [chiavi](#chiave) che verranno generate per il piano.

>![plan_designer.jpg](/mashery/plan_designer.jpg)
> *Dettaglio degli endpoint accessibili sottoscrivendosi al piano b2cws_dev*

> Non è possibile invocare gli endpoint esposti dal gateway senza prima aver creato un'applicazione, selezionato un piano di utilizzo e ricevuto una chiave con cui identificare le proprie chiamate. 
{.is-info}

## Chiave
Una [chiave](http://docs.mashery.com/design/GUID-B78424FD-C04D-4BBD-ACCA-73E0F6F90214.html) è una semplice stringa randomica alfanumerica generata dal gateway o inserita manualmente in fase di creazione. La chiave viene creata dopo aver selezionato una [applicazione](#applicazione) ed un [piano](#piano) e dovrà essere inclusa dai client in ogni chiamata al gateway così da identificarsi ed essere autorizzato all'accesso alle risorse specificate nel piano stesso.

>![package_keys.jpg](/mashery/package_keys.jpg)
> *Schermata di elenco delle chiavi. Come si può vedere ogni chiave è associata a una specifica applicazione, di conseguenza a un [utente](#utente), ma soprattutto a un [pacchetto](#pacchetto) e a un determinato piano di quel pacchetto.*

Una volta creata la chiave non è possibile modificarne il valore. È invece possibile modificare il piano associato a una chiave anche dopo la creazione della chiave stessa, purché il piano appartenga allo stesso pacchetto. A livello di chiave è anche possibile impostare dei valori di [throttling](#throttling) che vanno a sovrascrivere quelli specificati sull'[endpoint](#endpoint) e sul piano.

>![key.jpg](/mashery/key.jpg)
>*Dettaglio della configurazione di una chiave. *

> Per ogni combinazione applicazione-pacchetto può essere staccata una sola chiave. Se è richiesto avere due chiavi per due piani di uno stesso pacchetto sarà necessario creare due applicazioni separate.
{.is-warning}

>![members_applications_keys.jpg](/mashery/members_applications_keys.jpg)
> *Esempio di una possibile assegnazione di tre chiavi allo stesso utente. Come si può vedere possono essere staccate più chiavi per la stessa applicazione, purché esse facciano parte di pacchetti diversi.*

### Secret
Il secret è un'ulteriore stringa alfanumerica utilizzata per le implementazioni di autenticazione più complesse, ad esempio oAuth2. Analogamente alla chiave viene generato dal gateway e deve essere incluso nelle chiamate dei client. È possibile modificare il secret dal CC in ogni momento, contrariamente alla [chiave](#chiave) che una volta generata è immutabile.

## Documentazione Statica
La [**documentazione statica**](http://docs.mashery.com/manage/GUID-40EED8A4-4972-4183-975A-649AFF7B0BAD.html) (o *content*, utilizzando il generico termine scelto da Tibco) è l'insieme delle pagine web pubblicate sul [Developer Portal](/integration/tibcomashery/architecture#developer-portal) e consultabili dagli sviluppatori. Nella documentazione vengono fornite informazioni, guide e suggerimenti riguardanti il gateway, esempi di chiamate ai servizi pubblicati e quant'altro sia ritenuto utile alla dissemination dello strumento.

>![doc_page.jpg](/mashery/doc_page.jpg)
> *Esempio di documentazione statica*

Ad oggi l'unico modo per gestire la documentazione statica è tramite un editor (piuttosto buggato e con una user experience squisitamente anni 80) accessibile dal [Control Center](/integration/tibcomashery/architecture#control-center), che supporta HTML e Markdown. È anche fornito un primitivo *File Manager* che consente l'hosting di immagini e generici file sul portale. 

> Non è possibile agire sulla documentazione statica tramite la API di prodotto.
{.is-warning}


>![content_editor.jpg](/mashery/content_editor.jpg)
> *Editor dei contenuti del portale*
## Documentazione Interattiva
La [**documentazione interattiva**](http://docs.mashery.com/design/GUID-B0B8E8AF-AC34-44CE-950B-57D7103B0C0E.html), cui spesso Tibco si riferisce anche con il termine *IO-docs* e che impropriamente viene di solito chiamata *Swagger*, ha una sezione dedicata sul [Dev Portal](/integration/tibcomashery/architecture#developer-portal). In questa sezione, chiamata anche *API Console* per confondere ulteriormente le acque, una UI grafica di facile interpretazione presenta i seguenti elementi di ogni API agli sviluppatori:
- la struttura (quali sono i suoi endpoint e a cosa servono)
- il tipo di autorizzazione utilizzata
- i possibili codici d'errore restituiti e il loro significato
- l'interfaccia di input di ogni endpoint (quali parametri devono essere passati, quali sono opzionali, cosa rappresentano)
- l'interfaccia di output di ogni endpoint (quali parametri vengono passati nella risposta e in che modo)
- le strutture dati utilizzate (dette anche *definitions* usando la terminologia dello standard swagger o *models* secondo quella Tibco)

>![io_doc.jpg](/mashery/io_doc.jpg)
> *Documentazione interattiva di un semplice servizio REST con un singolo endpoint.*

La documentazione è definita interattiva perché è possibile preparare effettuare chiamate di test ai servizi senza dover uscire dal browser e ricevere risposte dal gateway, esattamente come se a chiamare fosse un "vero" client.

>![io_doc_exploded_ep.jpg](/mashery/io_doc_exploded_ep.jpg)
> *Dettaglio del singolo endpoint dopo che è stata effettuata una chiamata di test*

La UI utilizzata è un porting del progetto [SwaggerUI](https://swagger.io/tools/swagger-ui/).