---
title: Introduzione e oggetti di Mashery
description: 
published: true
date: 2021-03-04T10:21:49.465Z
tags: mashery, api, tibco, api gateway
editor: markdown
dateCreated: 2020-04-17T13:19:15.299Z
---

# Cosa è un API Gateway
Un API Gateway si occupa di fare da proxy tra i client che vogliono accedere alle risorse messe a disposizione dalle varie API e i sistemi di backend dove i servizi sono in esecuzione. Ciò significa che la funzione primaria del gateway è ricevere una chiamata da un client, smistarla verso il corretto backend di destinazione, ricevere la risposta e restituirla al client stesso.

>![api_gateway.jpg](/mashery/api_gateway.jpg){.align-center}
> *Schema di base del funzionamento di un API gateway*

Ovviamente questa è una visione semplicistica: lo strumento mette a disposizione una serie di [funzionalità](/integration/tibcomashery/features) aggiuntive.

# Oggetti
L'organizzazione logica interna di Mashery si basa su una serie di oggetti. Ogni oggetto ha degli attributi configurabili ed è collegato gerarchicamente ad altri oggetti.

>![objects.jpg](/mashery/objects.jpg)
> *Alcuni degli oggetti di Mashery con le rispettive relazioni*

Questi oggetti possono essere visti (poiché in effetti lo sono) come record di tabelle di un database.

>![ml_object.jpg](/mashery/ml_object.jpg)
> *Esempio di struttura di un oggetto Mashery, in questo caso il [Plan](#piano)*

Nei paragrafi seguenti verranno illustrati gli oggetti più importanti.

## Area

Quando viene effettuata una sottoscrizione a Mashery Tibco crea una **area** dedicata al cliente. Tutti gli oggetti verranno creati all'interno di questa area.

>![area.jpg](/mashery/area.jpg)
> *Dettaglio delle informazioni dell'area *pirelliapiportal**

Ogni area ha UUID e ID univoci che la identificano e possono essere utili in caso di contatti con il supporto.

## Organizzazione

Un'[**organizzazione**](http://docs.mashery.com/manage/GUID-EAD30F7B-689D-4BC5-9B25-28CD6BD400A7.html) è un contenitore di risorse (API, Pacchetti, Documentazione, ecc.) fra loro logicamente collegati. Ad esempio un'organizzazione può essere creata per raccogliere le risorse dedicate a una certa Business Unit del cliente oppure a un dato gruppo di lavoro. Tutte le organizzazioni sono figlie dell'area, l'organizzazione *root* all'interno della quale risiedono tutte le altre.

>![organizations.jpg](/mashery/organizations.jpg)
> *Esempio di struttura delle organizzazioni Mashery di un'ipotetica società*

In ogni organizzazione è possibile definire sotto-organizzazioni che funzionano esattamente come le organizzazioni stesse. Ad esempio nella già citata organizzazione dedicata a un gruppo di lavoro si potrebbe creare una sotto-organizzazione riservata ad uno specifico progetto in sviluppo. 

> Non è possibile scendere ulteriormente nell'albero, quindi il livello massimo è 3 (non esistono "sotto-sotto-organizzazioni").
{.is-info}

## Utente
Un oggetto [**utente**](http://docs.mashery.com/manage/GUID-7D08A6AC-E20B-43A5-B5E2-B3E5551087C6.html) viene creato:
- al momento della registrazione di un nuovo membro sul [Dev Portal](/integration/tibcomashery/architecture#developer-portal)
- manualmente da un amministratore nel [Control Center](/integration/tibcomashery/architecture#control-center).
- manualmente da un amministratore nell'area cloud Tibco (in questo caso si parla di *utenza cloud*)

L'utente è legato indissolubilmente a un indirizzo mail, tuttavia è concesso creare più utenti associati allo stesso indirizzo. Dopo la registrazione, se effettuata in *self-service*, verrà inviata una mail con un link di conferma prima di finalizzare la creazione.

>![users.jpg](/mashery/users.jpg)
> *Schermata del CC di elenco degli utenti appartenenti all'[area](#area)*

> La differenziazione tra utenze cloud e utenze "standard" nasce dal fatto che Mashery è stato integrato con l'area cloud Tibco solo successivamente all'acquisizione del prodotto. Le utenze cloud, contrariamente alle altre, possono essere configurate in [Single Sign-On](https://en.wikipedia.org/wiki/Single_sign-on) con la base utenti esistente del cliente ed hanno di default accesso al [Control Center](/integration/tibcomashery/architecture#control-center). Per questo motivo sono generalmente utilizzate come utenze amministrative.
{.is-info}

> Le utenze cloud presentano alcuni limiti, ad esempio se l'utenza viene "importata" via SSO nell'ecosistema Mashery le verrà assegnata come nome utente una stringa randomica che ne rende difficile l'identificazione rapida. Per ovviare a ciò si può utilizzare l'indirizzo mail come riferimento. **Inoltre le utenze cloud non possono essere utilizzate per invocare la [API di prodotto](/integration/tibcomashery/architecture#mashery-api), con l'unica eccezione del *serviceaccount* creato da Tibco.**
{.is-warning}

> **Le utenze "standard", invece, non possono avere privilegi di amministrazione a livello dell'intera area, ma solo su una o più [organizzazioni](/integration/tibcomashery/intro#organizzazione).** Sono quindi limitate nella loro visibilità degli oggetti sia sul CC che nelle invocazioni alla API Mashery.
{.is-warning}

> ![user_cloud_vs_cc.png](/mashery/user_cloud_vs_cc.png)
> *La stessa utenza cloud vista dal Tibco Cloud e dal Control Center dell'area; si possono notare lo username randomico e l'impossibilità di eliminarla dal CC*

> Una particolarità degli utenti Mashery è che sono salvati in uno spazio condiviso tra le aree dei vari clienti. Ciò significa che il campo *Username* deve essere necessariamente univoco sull'intero ambito del cloud Tibco, in caso contrario la creazione fallirà.
{.is-info}

## Ruolo
I **ruoli** assegnati all'[utente](#utente) Mashery determinano quali oggetti esso può vedere e/o modificare sia nel [Control Center](/integration/tibcomashery/architecture#control-center) che nel [Dev Portal](/integration/tibcomashery/architecture#developer-portal) che tramite [API di prodotto](/integration/tibcomashery/architecture#mashery-api).

#### Area Level Roles
Questi [ruoli](http://docs.mashery.com/manage/GUID-BC63BAB0-7BFE-4F0E-887F-CF32342F8F9E.html) riguardano esclusivamente il CC e possiamo definirli "Area Level" poiché determinano la visibilità a livello dell'intera area cliente. (https://docs.mashery.com/manage/GUID-C3515849-9ADF-4673-9D02-EC3E54A22134.html).
> Gli Area Level Roles non possono essere assegnati dal CC stesso, si assegnano dal cloud Tibco. Sono quindi riservati a utenze di tipo cloud.
{.is-warning}

>![area_roles.jpg](/mashery/area_roles.jpg)
> *Schermata di assegnazione degli Area Level Roles*

#### Organization Roles
Per ogni organizzazione creata Mashery genera automaticamente una serie di [ruoli](http://docs.mashery.com/manage/GUID-EAD30F7B-689D-4BC5-9B25-28CD6BD400A7.html), analoghi ai precedenti, con la differenza che in questo caso la visibilità sul CC e tramite API è limitata agli oggetti appartenenti a una determinata organizzazione.

>![org_roles.jpg](/mashery/org_roles.jpg)
> *Schermata di assegnazione degli Organization Roles per un utente*

#### Portal Access Groups
Come suggerito dal nome Tibco li considera "gruppi", non ruoli, tuttavia hanno la stessa funzione e le stesse caratteristiche. Determinano la visibilità da parte dei developer degli unici oggetti da loro fruibili sul [Developer Portal](/integration/tibcomashery/architecture#developer-portal), cioè [piani](#piano) e [documentazione interattiva](#documentazione-interattiva). Sono customizzabili: vengono creati con un nome a piacere tramite il CC ed è possibile definire liberamente quali utenti ne fanno parte e a quali risorse hanno accesso.

>![access_groups.jpg](/mashery/access_groups.jpg)
> *Dettaglio di un gruppo d'accesso e delle risorse correlate*

> I seguenti ruoli sono utilizzabili, pur non essendo citati dalla documentazione ufficiale:
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

Nel piano è definita una lista di [API](#api)/[endpoints](#endpoint)/[metodi](#metodo) (la granularità è configurabile a piacere) a cui il piano stesso dà diritto di accesso. Oltre a ciò a questo livello possono essere definiti i limiti di [throttling](/integration/tibcomashery/features#throttling) e alcune proprietà delle [chiavi](#chiave) che verranno generate per il piano.

>![plan_designer.jpg](/mashery/plan_designer.jpg)
> *Dettaglio degli endpoint accessibili sottoscrivendosi al piano b2cws_dev*

> Non è possibile invocare gli endpoint esposti dal gateway senza prima aver creato un'[applicazione](#applicazione), selezionato un piano di utilizzo e ricevuto una chiave con cui identificare le proprie chiamate. 
{.is-info}

## Chiave
Una [chiave](http://docs.mashery.com/design/GUID-B78424FD-C04D-4BBD-ACCA-73E0F6F90214.html) è una semplice stringa randomica alfanumerica generata dal gateway oppure inserita manualmente da un amministratore in fase di creazione. La chiave viene creata dopo aver selezionato una [applicazione](#applicazione) ed un [piano](#piano) e dovrà essere inclusa dai client in ogni chiamata al gateway così da identificarsi ed essere autorizzato all'accesso alle risorse specificate nel piano stesso.

>![package_keys.jpg](/mashery/package_keys.jpg)
> *Schermata di elenco delle chiavi. Come si può vedere ogni chiave è associata a una specifica applicazione, di conseguenza a un [utente](#utente), ma soprattutto a un [pacchetto](#pacchetto) e a un determinato piano di quel pacchetto.*

Una volta creata la chiave non è possibile modificarne il valore. È invece possibile modificare il piano associato a una chiave anche dopo la creazione della chiave stessa, purché il piano appartenga allo stesso pacchetto. A livello di chiave è anche possibile impostare dei valori di [throttling](/integration/tibcomashery/features#throttling) che vanno a sovrascrivere quelli specificati sull'[endpoint](#endpoint) e sul piano.

>![key.jpg](/mashery/key.jpg)
>*Dettaglio della configurazione di una chiave.*

> Per ogni combinazione applicazione-pacchetto può essere staccata una sola chiave. Se è richiesto avere due chiavi per due piani di uno stesso pacchetto sarà necessario creare due applicazioni separate.
{.is-warning}

>![members_applications_keys.jpg](/mashery/members_applications_keys.jpg)
> *Esempio di una possibile assegnazione di tre chiavi allo stesso utente. Come si può vedere possono essere staccate più chiavi per la stessa applicazione, purché esse facciano parte di pacchetti diversi.*

### Secret
Il secret è un'ulteriore stringa alfanumerica utilizzata per le implementazioni di autenticazione più complesse, ad esempio oAuth2. Analogamente alla chiave viene generato dal gateway e deve essere incluso nelle chiamate dei client. È possibile modificare il secret dal CC in ogni momento, contrariamente alla [chiave](#chiave) che una volta generata è immutabile.

## Documentazione Statica
La [**documentazione statica**](http://docs.mashery.com/manage/GUID-40EED8A4-4972-4183-975A-649AFF7B0BAD.html) (o *content*, utilizzando il generico termine scelto da Tibco) è l'insieme delle pagine web custom pubblicate sul [Developer Portal](/integration/tibcomashery/architecture#developer-portal) e consultabili dagli sviluppatori. Lo scopo della documentazione è fornire informazioni, guide e suggerimenti riguardanti il gateway, esempi di chiamate ai servizi pubblicati e quant'altro sia ritenuto utile alla dissemination e adoption dello strumento.

>![doc_page.jpg](/mashery/doc_page.jpg)
> *Esempio di documentazione statica*

Ad oggi l'unico modo per gestire la documentazione statica è tramite un editor (piuttosto buggato e con user-experience squisitamente anni 80) accessibile dal [Control Center](/integration/tibcomashery/architecture#control-center), che supporta HTML e Markdown. È anche disponibile un primitivo *File Manager* che consente l'hosting di immagini e altri tipi di file sul portale. 

> Non è possibile agire sulla documentazione statica tramite la API di prodotto.
{.is-warning}


>![content_editor.jpg](/mashery/content_editor.jpg)
> *Editor dei contenuti del portale*
## Documentazione Interattiva
La [**documentazione interattiva**](http://docs.mashery.com/design/GUID-B0B8E8AF-AC34-44CE-950B-57D7103B0C0E.html), cui spesso Tibco si riferisce anche con il termine *IO-docs* e che impropriamente viene di solito chiamata *Swagger*, ha una sezione dedicata sul [Dev Portal](/integration/tibcomashery/architecture#developer-portal). In questa sezione, definita *API Console* per confondere ulteriormente le acque, una UI grafica presenta i seguenti elementi di ogni API agli sviluppatori:
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

# Connectors / Adapters

> La sottile differenza tra *Connector* e *Adapter* così come da documentazione (gli uni sono standard e forniti da Tibco, gli altri sono custom e sviluppati ad-hoc da Tibco stessa o dal cliente) esiste e ne prendiamo atto. Nella realtà i due termini vengono utilizzati indifferentemente in maniera interscambiabile, così come (più raramente) il termine *Processor*, poiché si riferiscono ad oggetti che hanno esattamente le stesse funzionalità.
{.is-info}

Un [connector](http://docs.mashery.com/connectorsguide/GUID-B02231FF-9254-435D-8F54-EC3F4AD4792E.html) è una semplice classe Java innestata come plug-in sul runtime di Mashery e si occupa di processare/trasformare le chiamate "in volo" mentre transitano dal gateway. Il connector è essenzialmente la risposta di Tibco alla domanda *"Perché Mashery non mi fa la spremuta? Il commerciale aveva detto che si poteva!"*.

>![use-case.jpg](/mashery/use-case.jpg)
> *Certo, si può fare, ma ciò non significa che sia una buona idea*

I connector sono modulari e conferiscono al prodotto una elasticità di utilizzo maggiore consentendogli appunto di adattarsi a richieste fuori dal comune. Alcune delle applicazioni più frequenti sono use-case che richiedono di trasformare il payload di una chiamata. 
> In linea di massima è fuori dallo scope del gateway interferire con il contenuto delle chiamate e Mashery non se ne occupa affatto, con le seguenti rare eccezioni:
>
> • se la chiave/token di autenticazione si trova nel payload
> • se si utilizzano i [metodi](#metodo) e l'identificativo del metodo si trova nel payload
> • se sono configurati dei *[Response Filters](integration/tibcomashery/features#response-filters)*
> • se si attiva la funzionalità di *[Verbose Logging](https://docs.tibco.com/pub/mash-local/latest/doc/html/GUID-D3939B05-7202-42B9-8C56-EA7035432D9B.html)* in Mashery Local o il *[Call Inspector](http://docs.mashery.com/analyze/GUID-402C28D5-283F-4AFD-9436-F0550A685F0A.html)* per Mashery Cloud
{.is-info}

Sottolineiamo tuttavia che gli adapter non hanno come unica applicazione la trasformazione del payload ma possono anche effettuare processing di altro tipo (autenticazione custom, arricchimento/modifica degli headers, instradamento condizionale, ...). Queste elaborazioni possono essere effettuate sia durante il transito della chiamata dal client verso il backend (in questo caso si parla di *pre-processing*) che durante il transito della risposta dal backend verso il client (*post-processing*).

L'adapter si abilita esclusivamente sull'oggetto [endpoint](#endpoint), va quindi abilitato più volte in caso lo si voglia applicare a un intera [API](#api). Se necessario è possibile anche specificare, sempre associandoli all'endpoint, dei dati di configurazione aggiuntivi da fornire come input all'adapter stesso.

>![adapter.jpg](/mashery/adapter.jpg)
> *Schermata di configurazione degli adapter di un endpoint*

Poiché è possibile che su un dato endpoint siano richieste funzionalità fornite da più adapter diversi è anche possibile effettuare il cosiddetto [*chaining*](http://docs.mashery.com/connectorsguide/GUID-8CB3A085-4F25-4294-8756-E730191C1D46.html), cioè di configurarli in cascata.

> Gli adapter forniti da Tibco (cioè i connector, seguendo la nomenclatura ufficiale) sono immediatamente disponibili su tutti i Traffic Manager cloud previa configurazione dell'endpoint. Per parte di questi connector sono state anche rilasciate le classi Java, a fine 2019, ed è quindi possibile l'installazione sui TM local. Al contrario tutti i connector più recenti sono ad oggi (maggio 2020) disponibili esclusivamente in cloud.
{.is-info}

## Extended Attribute Values (EAVs)

Gli EAV sono una feature (ad oggi) completamente non documentata da Tibco che permette di estendere considerevolmente la funzionalità di un adapter. 

> Ci sono riferimenti all'esistenza degli EAV nella documentazione dei vari connector ma non ne viene mai spiegata la natura o il funzionamento. Ciò è dovuto presumibilmente alla volontà più o meno esplicita di Tibco di mantenere *in-house* le conoscenze necessarie per sviluppare connectors più avanzati e/o allo scarso numero di clienti che ne fanno uso.
{.is-info}

Gli EAV sono racchiusi in uno dei campi (di tipo *longtext*) associati agli [oggetti](#oggetti) interni al gateway e permettono di attribuire informazioni aggiuntive all'oggetto stesso. All'interno dal campo Tibco ha previsto una struttura XML in modo da poter inserire EAV multipli senza dover aggiungere altri campi all'oggetto.

>![eav_example.jpg](/mashery/eav_example.jpg)
> *Esempio di EAV associato ad una [chiave](#chiave): in questo caso l'EAV è stato utilizzato per racchiudere una whitelist di hostname e IP associati alla chiave stessa*

Come già accennato un adapter, di base, può accedere esclusivamente alle informazioni configurate sull'[endpoint](#endpoint); tramite l'utilizzo degli EAV invece l'adapter può estrarre informazioni da altri oggetti e utilizzarle per implementare logiche più complesse.

L'aggiunta di EAV in modalità [cloud](/integration/tibcomashery/architecture#cloud) o [tethered](/integration/tibcomashery/architecture#hybrid) richiede obbligatoriamente il passaggio da Tibco poiché tutte le configurazioni, incluso il popolamento degli EAV, vengono effettuate sul CC (e quindi sincronizzate con il local, in caso di modalità tethered).

>![eav_creation_info_example.jpg](/mashery/eav_creation_info_example.jpg)
> *Lista delle informazioni che devono/possono essere fornite a Tibco in fase di creazione di un EAV*

Una volta creato l'EAV sarà visibile e modificabile dalla sezione del CC dedicata all'oggetto corrispondente.

>![eav_config_example.jpg](/mashery/eav_config_example.jpg)
> *Esempio di schermata di configurazione degli EAV di una chiave: come evidente da un confronto con lo screenshot precedente Tibco ha utilizzato il Name al posto della Label e ha ignorato la Description fornita*

L'aggiunta e la gestione deli EAV in caso di modalità [untethered](/integration/tibcomashery/architecture#untethered) va invece gestita andando ad operare direttamente sul mysqlDB di prodotto.