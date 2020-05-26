---
title: Funzionalità di prodotto
description: 
published: true
date: 2020-05-26T13:43:34.178Z
tags: mashery, tibco, api gateway
---

Nelle sezioni successive sono dettagliate le macro funzionalità che Tibco Mashery mette a disposizione di un cliente per implementare la sua API governance.

## Autenticazione & Autorizzazione
Una delle funzionalità più importanti, se non la più importante, che il gateway fornisce è l'abilità di accertare l'identità dei chiamanti (**autenticazione**) e stabilire di conseguenza a quali risorse essi abbiano eventualmente accesso (**autorizzazione**). Per fare ciò Mashery mette a disposizione diversi metodi.

> In Mashery l'autenticazione deve essere impostata su ogni singolo [endpoint](/integration/tibcomashery/intro#endpoint), non è possibile agire sull'intera [API](/integration/tibcomashery/intro#api).
{.is-info}

> In Mashery deve **sempre** essere impostata un'autenticazione su ogni endpoint, perché il gateway deve necessariamente essere in grado di identificare il chiamante. La possibilità di avere endpoint non autenticati (*noauth*) esiste ma va realizzata tramite un tipico [*Tibco Beardtrick*](#INSERIRELINK) alquanto posticcio (è stato evidentemente aggiunto in corsa su richiesta dei clienti).
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
Una volta che il gateway è in grado di [identificare](#autenticazione-autorizzazione) con certezza il client associato ad ogni chiamata il logico step successivo è mantenere un registro delle richieste con il maggior numero di informazioni possibili, tra cui ovviamente chi ha invocato quale endpoint e in quale momento.
Per fare ciò Mashery produce [*access logs*](/integration/tibcomashery/mladministration#access-logs) interni che possono essere consultati direttamente (principalmente per finalità di debugging) e/o rediretti verso piattaforme di log management di terze parti in modo da essere categorizzati, trasformati e resi più fruibili ai fini statistici.

### Executive Summary
L'[Executive Summary](http://docs.mashery.com/analyze/GUID-C4E657F4-34A7-4788-B08B-F6738C7A3CB8.html) è una sezione del [Control Center](/integration/tibcomashery/architecture#control-center) che consente una visione ad altissimo livello di alcune statistiche d'uso relative all'[area](/integration/tibcomashery/intro#area). E' ben documentato e non c'è molto da aggiungere qui se non che i tempi di caricamento delle singole view sono molto lunghi, soprattutto selezionando archi temporali ampi.

> ![executive_summary.jpg](/mashery/executive_summary.jpg)
> *Executive summary per l'area pirelliapiportal*

### Reports
La sezione dedicata ai [Reports](http://docs.mashery.com/analyze/GUID-98A019E2-0870-4D34-B23E-39B41A535114.html) nel [Control Center](/integration/tibcomashery/architecture#control-center) presenta una serie di dashboard dalle quali è possibile estrapolare informazioni d'uso più capillari con focus sui singoli [package](/integration/tibcomashery/intro#pacchetto) o sui singoli [servizi](/integration/tibcomashery/intro#api).

![reports.jpg](/mashery/reports.jpg)

I principali svantaggi di questa dashboard fornita out-of-the-box sono la lentezza di caricamento delle singole view e l'impossibilità di esportare i dati integralmente (è solo possibile scaricare i dati di ogni singola view). Inoltre la GUI è decisamente spartana e non è dato customizzare la dashboard in alcun modo: si è limitati a quello che Tibco mette a disposizione.

### Piattaforme di Log Management
Mashery fornisce nativamente la possibilità di instradare puntualmente i log di prodotto a piattaforme di log management (elastic, splunk, kafka, ...) sia in un deployment [Cloud](/integration/tibcomashery/architecture#cloud) che [Local](/integration/tibcomashery/architecture#local).

Nel caso di un gateway cloud (tecnicamente anche local, ma solo in modalità hybrid/tethered) ciò è implementabile in maniera sincrona tramite la funzionalità di [Call Log Streams](http://docs.mashery.com/analyze/GUID-A085F6A2-AE7A-4D8F-9CA7-63D0DEBE2512.html) che trasmette puntualmente ogni log ad un endpoint di ingestion per mezzo di un WebSocket. Sono tuttavia possibili ritardi anche di svariati minuti tra una chiamata e la trasmissione del corrispondente log in formato JSON.

>![wss_logs.jpg](/mashery/wss_logs.jpg)
> *Esempio di log stream catturato tramite un WebSocket client di test*

Nel caso invece di un deployment local, sia untethered che hybrid, è il componente Log Service che si occupa dell'instradamento dei log verso una piattaforma esterna, purché vengano effettuate le necessarie [configurazioni](https://docs.tibco.com/pub/mash-local/latest/doc/html/GUID-7FE86E9D-943C-427C-98AA-C11B37BABBCF.html). Anche in questo caso i log vengono trasmessi in formato JSON, tuttavia il ritardo di trasmissione è di pochi secondi.

>![elastic_log.jpg](/mashery/elastic_log.jpg)
> *Esempio di document elastic derivato da un singolo log Mashery*

> Sia utilizzando la funzionalità di Call Log Streams che configurando Mashery Local per instradare i log ad oggi non è possibile in alcun modo modificare la struttura dei log stessi (aggiungere/rimuovere campi, ad esempio).
{.is-info}

## Filtro delle chiamate
Uno schermo di sicurezza aggiuntivo, che in realtà Mashery non fornisce out-of-the-box ma solamente tramite l'utilizzo di [adapters](/integration/tibcomashery/intro#connectors-adapters), prevede la possibilità di permettere o negare l'accesso ai servizi implementando logiche di business. Questo filtro si può aggiungere all'[autenticazione](#autenticazione-autorizzazione) oppure essere stand-alone (in questo caso gli endpoint tecnicamente saranno non autenticati, cioè in [*noauth*](#inserire-link)).

È possibile permettere accesso solo a determinati IP ([IP Whitelisting Connector](http://docs.mashery.com/connectorsguide/GUID-1BEA3681-0C40-4398-8FED-1CB4F4A52942.html)) oppure al contrario negare accesso agli IP indesiderati ([IP Blocking Connector](http://docs.mashery.com/connectorsguide/GUID-3290F176-44C5-4D95-9DA1-4141B85B7FB7.html)). Alcuni connectors consentono anche di implementare filtri basati sulla chiamata stessa, ad esempio il [Whitelisting Connector](http://docs.mashery.com/connectorsguide/GUID-F3B0C216-9D0B-4BE1-A6A1-C789FD7576CA.html) e il [Block API Connector](http://docs.mashery.com/connectorsguide/GUID-74511B0B-CFB7-42AA-BAA8-C66F10E06151.html).

> La stragrande maggioranza dei connettori forniti da Tibco può recepire input configurati esclusivamente sull'oggetto [endpoint](/integration/tibcomashery/intro#endpoint). Ciò significa che le logiche saranno implementate *in toto* su tutte le chiamate in ingresso a un determinato endpoint e non, ad esempio, basandosi sull'identità del chiamante (per fare ciò occorrerebbe che il connettore leggesse informazioni dalla [chiave](/integration/tibcomashery/intro#chiave) associata alla chiamata).
Un workaround a questo limite è lo sviluppo di adapter custom che sfruttino gli [EAV](/integration/tibcomashery/intro#extended-attribute-values-eavs) (Extended Attribute Values).
{.is-warning}

## Rate Limiting
Mashery prevede due attributi separati per gestire il flusso delle chiamate: il **Throttle** e la **Quota**. 

>![plan_rate_limits.jpg](/mashery/plan_rate_limits.jpg)
> *Schermata di configurazione di throttle e quota sul [piano](/integration/tibcomashery/intro#piano)*

### Throttle
Il **throttle** permette di impostare un limite sulle QPS (*Queries Per Second*), cioè sulle chiamate al secondo servite. Si tratta quindi di un vincolo sul *burst* concepito per evitare di sottoporre a un carico eccessivo sia il gateway stesso che, soprattutto, il backend che eroga il servizio.
Se un client supera il limite di QPS consentite riceverà una risposta di errore a tutte le chiamate in eccesso effettuate in quel dato secondo. Il secondo successivo il contatore verrà azzerato e potranno di nuovo essere effettuate chiamate.

>![over_qps_error.jpg](/mashery/over_qps_error.jpg)
> *Esempio di risposta di errore restituita dal gateway in caso di superamento del limite di QPS*

### Quota
La **quota** è un limite customizzabile di chiamate consentite nell'unità di tempo, che può essere *minuto*, *ora*, *giorno*, *mese* se configurata sul piano oppure obbligatoriamente *giorno* se configurata sulla singola chiave. Si tratta di un vincolo concepito per regolare il numero di chiamate che uno specifico client può effettuare, specialmente in ottica di monetizzazione dei servizi.
Se il client supera la quota a lui allocata riceverà una risposta di errore e dovrà attendere lo scadere dell'unità di tempo configurata prima di effettuare con successo ulteriori chiamate.

>![over_quota_error.jpg](/mashery/over_quota_error.jpg)
> *Esempio di risposta di errore restituita dal gateway in caso di superamento della quota*

> Le chiamate bloccate per superamento del limite di QPS non vengono conteggiate tra quelle consentite nella quota.
{.is-info}

### Gerarchia delle configurazioni
I valori di throttle e quota possono essere configurati:

- sul [piano](/integration/tibcomashery/intro#api), andando così ad avere effetto sulle chiamate autenticate con tutte le chiavi associate al piano stesso 
- sulla singola [chiave](/integration/tibcomashery/intro#chiave), andando a sovrascrivere, per la chiave in questione, i valori definiti nel piano

>![key_rate_limits.jpg](/mashery/key_rate_limits.jpg)
> *Schermata di configurazione di throttle e quota sulla [chiave](/integration/tibcomashery/intro#chiave)*

Il Throttle può anche essere impostato sulla [API](/integration/tibcomashery/intro#api), andando a limitare il volume di traffico globale in ingresso a tutti gli endpoint del servizio.

>![api_rate_limits.jpg](/mashery/api_rate_limits.jpg)
> *Schermata di configurazione del throttle sulla [API](/integration/tibcomashery/intro#api)*

> Mashery non imposta alcun limite predefinito sulla API. Vengono invece impostati un throttle di **2 QPS** e una quota di **5000 chiamate al giorno** sul piano al momento della creazione. Ogni nuova chiave è configurata di default per rispettare i limiti impostati sul piano. 
{.is-warning}

## Notifiche di eventi
### Notifiche developer
Ogni [sviluppatore](/integration/tibcomashery/intro#utente) registrato al [portale](/integration/tibcomashery/architecture#developer-portal) riceve una [mail](http://docs.mashery.com/manage/GUID-B28B2B09-BAD3-464F-882A-5F58050AFECE.html) di notifica:

- al momento della registrazione, con un link di conferma per finalizzare la creazione della sua utenza.
>![new_user_mail.jpg](/mashery/new_user_mail.jpg)
- in caso di richiesta di reset della password o recupero dell'username, con un link per completare l'operazione.
>![reset_password_mail.jpg](/mashery/reset_password_mail.jpg)
- al momento della creazione di una nuova [applicazione](/integration/tibcomashery/intro#applicazione) e contestuale richiesta di una [chiave](/integration/tibcomashery/intro#chiave).
>![new_app_mail.jpg](/mashery/new_app_mail.jpg)

Il testo delle mail è personalizzabile (eccetto per quelle di reset e recupero credenziali), così come l'indirizzo di provenienza (ma solo previa approvazione di Tibco del nuovo indirizzo).

### Notifiche amministrative
Gli amministratori del gateway possono scegliere di ricevere notifiche quando si verificano alcuni eventi rilevanti. Per l'elenco degli eventi riferirsi alla [documentazione](http://docs.mashery.com/manage/GUID-F23492B4-F99C-447B-B83A-06189667A6F7.html).

> ![new_app_adm_mail.jpg](/mashery/new_app_adm_mail.jpg)
> *Esempio di notifica amministrativa per la creazione di una nuova applicazione*

### Notifiche di utilizzo
Sul [pacchetto](/integration/tibcomashery/intro#pacchetto) è possibile abilitare delle mail di notifica, sia per i developer che per gli amministratori, in caso il [rate limiting](#rate-limiting) venga oltrepassato o sia in procinto di esserlo.
La [documentazione](http://docs.mashery.com/design/GUID-AEDA788C-A160-4311-AF3C-04390228E984.html) a riguardo è chiara e completa, quindi si rimanda a quella per ulteriori approfondimenti.



Anche in questo caso è possibile [personalizzare](http://docs.mashery.com/design/GUID-2E5BD78C-4D01-492B-AD0A-128CCD93038B.html) i template delle mail, associandoli ad ogni singolo [piano](/integration/tibcomashery/intro#piano).

### Event Trigger API

## Caching
## Processing delle chiamate
## Documentazione e divulgazione delle API
## Organizzazione gerarchica degli oggetti
## Amministrazione *self-service* degli oggetti