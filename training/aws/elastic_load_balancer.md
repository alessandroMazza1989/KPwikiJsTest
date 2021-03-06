---
title: Elastic Load Balancer
description: 
published: true
date: 2021-04-07T12:28:34.426Z
tags: aws, cloud, networking, security, elastic load balancer, load balancer
editor: markdown
dateCreated: 2021-03-08T10:08:28.825Z
---

# Elastic Load Balancer

Un **load balancer** è un meccanismo che automaticamente **distribuisce** il traffico tra istanze EC2 multiple.

E’ possibile usare il proprio load balancer, installato su un’istanza EC2, oppure utilizzare il servizio **AWS ELB**, che offre **un load balancer gestito** da utilizzare facilmente.

ELB consente di distribuire il traffico verso le istanze EC2 di _una o più AZ_, consentendo di erogare applicazioni ad **alta disponibilità**.

ELB supporta **routing e load balancing** dei protocolli **HTTP, HTTPS, TCP e SSL**.

ELB fornisce un **singolo entry point** per la configurazione del DNS e supporta un bilanciamento **sia Internet-facing che Application-facing**.

ELB supporta gli **health checks** sulle istanze EC2 affinché il traffico non venga inoltrato verso istanze non in salute.

ELB può **scalare automaticamente** sulla base delle metriche che colleziona.

ELB si integra con **AutoScaling** per **scalare automaticamente le istanze EC2** dietro al balancer stesso.

Infine, ELB è sicuro, lavora con VPC per dirigere il traffico internamente tra applicazioni private, **esponendo solo gli IP pubblici** delle applicazioni Internet-facing.

ELB supporta inoltre la **gestione dei certificati SSL**.

## Types of Load Balancers

### Application Load Balancer

Un **Application Load Balancer** funziona a **livello di applicazione**, il **settimo livello** del modello _Open Systems Interconnection (OSI)_.

Una volta che il sistema di bilanciamento del carico ha ricevuto una richiesta, valuta le **regole del listener** in ordine di _priorità_ per determinare quale di esse applicare, quindi seleziona un target dal gruppo di target per l'operazione della regola.

È possibile configurare le regole del listener per instradare le richieste su **diversi** gruppi di destinazioni **in base al contenuto del traffico** delle applicazioni.

L'instradamento avviene in maniera **indipendente** per ogni gruppo di destinazioni, anche nel caso in cui una destinazione sia registrata con più gruppi.

È possibile configurare l'algoritmo di instradamento utilizzato a livello di gruppo di target. 
L'algoritmo di instradamento predefinito è **round robin**;

### Network Load Balancer

**Network Load Balancer** funziona al **quarto livello** del modello _Open Systems Interconnection (OSI)_.

È in grado di gestire **milioni di richieste al secondo**. Dopo aver ricevuto una richiesta di connessione, il sistema di bilanciamento del carico seleziona un target dal gruppo target per la regola predefinita. 

Tenta quindi di aprire una connessione TCP per la destinazione selezionata sulla porta specificata nella configurazione del listener.

Quando si abilita una Availability Zone per il sistema di bilanciamento del carico, Elastic Load Balancing **crea un nodo** del sistema di bilanciamento nella AZ.

Per impostazione predefinita, ogni nodo del sistema di bilanciamento del carico distribuisce il traffico _solo_ tra i target registrati nella AZ del sistema.

Se attivi il bilanciamento del carico su più zone, ogni nodo di bilanciamento del carico distribuisce le richieste nei target registrati in _tutte_ le AZ

### Gateway Load Balancer

Un Gateway Load Balancer opera al **terzo livello** del modello _OSI (Open Systems Interconnection)_, il livello di rete. Ascolta tutti i pacchetti IP su tutte le porte e inoltra il traffico al gruppo di destinazione specificato nella regola del listener.

Ascolta i **pacchetti IP** su tutte le porte e inoltra il traffico al gruppo di destinazione specificato nella regola del listener.

## Configuring Elastic Load Balancing

ELB consente di configurare molti aspetti del balancer, che vediamo di seguito.

### Idle Connection Timeout

Per ogni richiesta che un client fa verso un load balancer, il balancer mantiene **2 connessioni**: una con il client e l’altra con l’istanza di backend.

Per ogni connessione, il balancer gestisce un **“idle timeout”** che viene triggerato se non viene ricevuto alcun dato su quella connessione per uno specifico periodo di tempo. Superato questo limite, il balancer termina la connessione.

Di default ELB imposta il timeout a 60 secondi per entrambe le connessioni. Se una richiesta HTTP non riceve risposta entro questo tempo, il balancer butta giù la connessione anche se ci sono dati che sono ancora in trasferimento. E’ possibile ovviamente modificare l’impostazione.

Se si utilizzano listener HTTP o HTTPS, si raccomanda di utilizzare l’opzione **“keep-alive”** sui web server delle istanze EC2. 

Quando abilitato, consente al load balancer di riusare le connessioni verso le istanze di backend in modo da ridurre il consumo di CPU.
NB.: _assicurarsi che il valore “keep-alive” sia maggiore del valore di “idle-timeout”_.

### Cross-Zone Load Balancing

Per assicurare che le richieste vengano inviate a tutte le istanze disponibili registrate sotto il balancer, in qualsiasi AZ esse siano, va abilitato il **cross-zone load balancing**.

Questa impostazione elimina inoltre la necessità di mantenere un numero equivalente di istanze in ogni AZ.

### Connection Draining

Per assicurare che il load balancer smetta di inviare richieste alle istanze che si stanno deregistrando dal balancer o che non sono in salute, ma provi comunque a terminare le connessioni ancora aperte, va abilitata il “**connection draining**”.

Quando si abilita, si può specificare il **tempo massimo** in cui il load balancer tiene attive le connessioni prima di dichiarare un’istanza **deregistrata**.

Il tempo è configurabile tra 1 e 3600 secondi (default è 300 secondi).

### Proxy Protocol

Quando si utilizza TCP o SSL sia per connessioni frontend che backend, il load balancer inoltra le richieste alle istanze di backend _senza modificare gli header_.

Se si abilita il **Proxy Protocol**, un header human-readable viene aggiunto alle richieste con informazioni di connessione.

_Verificare_ che il load balancer _non sia_ dietro un proxy server con Proxy Protocol abilitato altrimenti vengono aggiunti 2 header di questo tipo e potrebbe esserci qualche problema.

### Sticky Sessions

Di default, un load balancer redirige le richieste _verso le istanze con minor carico_.

E’ possibile però utilizzare la feature **sticky session** per fare in modo che il balancer provi a inoltrare tutte le richieste appartenenti ad una stessa sessione utente verso la stessa istanza.

Il punto è capire per quanto tempo il load balancer debba eseguire questo “binding”. Se l’applicazione utilizza i suoi **session cookie**, si può impostare ELB per eseguire tale binding per il tempo di sopravvivenza di tali cookie.

Se l’applicazione non ha cookie propri, si può specificare la durata manualmente. 
ELB _crea un cookie_ nominato **AWSELB** che viene utilizzato per mappare la sessione.

### Health Checks

ELB supporta gli **health checks** per testare lo stato delle istanze EC2. Lo stato delle istanze in salute è **InService** mentre per quelle ko è **OutOfService**.

Il load balancer esegue gli health checks periodicamente su tutte le istanze registrate.

Un health check può essere:
- un **ping**;
- un **connection attempt**;
- una pagina verificata periodicamente;

L’intervallo con cui effettuare i check è configurabile, così come il massimo tempo di attesa e il massimo numero di tentativi oltre il quale dichiarare un’istanza **OutOfService**.

## References
- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html