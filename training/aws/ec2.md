---
title: Amazon EC2
description: 
published: true
date: 2021-03-17T16:12:38.303Z
tags: aws, cloud, compute, ec2, auto-scaling, auto scaling
editor: markdown
dateCreated: 2021-03-08T11:06:36.551Z
---

# Amazon Elastic Compute Cloud (EC2)

Amazon EC2 è un servizio che offre capacità di calcolo nel cloud.

## Compute Basics

“Compute” significa la capacità di potenza richiesta per soddisfare un workload.
EC2 consente di avere capacità di calcolo grazie all’utilizzo di istanze EC2.
Ci sono 2 concetti chiave nell’utilizzo di istanze EC2:
- le risorse hardware dedicate all’istanza;
- il software installato sull’istanza;

## Instance Types

Il tipo di istanza definisce l’hardware virtuale a disposizione su un’istanza EC2. Ci sono moltissime tipologie di istanze disponibili, che variano rispetto a:
- Virtual CPUs;
- Memory;
- Storage;
- Network performance;

Le tipologie di istanze sono raggruppate in **famiglie**, sulla base della proporzione dei valori delle dimensioni appena citate.

All’interno della stessa famiglia ci sono diverse tipologie di istanze (t1.micro, t1.small, etc.).
Le network performance crescono al crescere delle altre risorse.

Per applicazioni che necessitano maggiori performance di rete, EC2 offre l’ **”enhanced networking”**, che riduce l’impatto della virtualizzazione abilitando una capability chiamata **Single Root I/O Virtualization (SR-IOV)**. Questo consente:

- un maggior numero di Packets Per Second (PPS);
- minor latenza;
- meno rumore si segnale (jitter). 

L’enhanced networking è disponibile solo per istanze lanciate _all’interno_ di una VPC.

## Amazon Machine Images (AMI)

AMI definisce il software iniziale che verrà installato **al momento del lancio** di un’istanza EC2, in termini di:

- Sistema operativo e configurazioni;
- patches;
- applicazioni o software di sistema;

Tutte le AMI sono basate su sistemi a 86 bit, Linux o Windows.

Ci sono 4 tipologie di AMI:
1. **Pubblicate da AWS**: corrispondono sostanzialmente a immagini di Sistemi Operativi;
2. **Pubblicate su Marketplace AWS**: contengono sistema operativo e qualsiasi altro software che il creatore della AMI ha deciso di installare;
3. **Generate da istanze esistenti**: è il caso in cui si installa tutto ciò che si vuole e poi si pubblica l’AMI, o sul marketplace o per uso futuro;
4. **Uploaded Virtual Servers**: tramite il servizio di AWS VM Import/Export è possibile creare immagini da vari formati di virtualizzazione, incluso raw, VHD, VMDK, OVA.

## Securely Using an Instance

Una volta lanciata, l’istanza può essere gestita tramite internet. AWS ha diversi servizi e funzionalità per assicurare che questo venga fatto in modo semplice.

Addressing an Instance
- **Public Domain Name System (DNS)** Name: quando si lancia un’istanza, AWS crea un DNS name che può essere utilizzato per accedere all’istanza, che rimane tale solo fino a quando l’istanza rimane running e non può essere trasferito ad un’altra istanza;
- **Public IP**: così come ogni istanza ha un DNS Name, ha anche un IP pubblico che segue le stesse regole del DNS Name;
- **Elastic IP**: un Elastic IP consente di associare un IP fisso ad un’istanza, che rimane attached anche quando l’istanza viene spenta.

## Initial Access

EC2 utilizza la crittografia a **chiave pubblica-privata** per criptare e decriptare le informazioni di login.

La coppia di chiavi si chiama **“key pair”** e possono essere create su AWS Console, tramite CLI o API, o è possibile uploadare la propria coppia di chiavi.

Quando viene lanciata un’istanza Windows, EC2 genera una password random per l’amministratore locale e cripta la password utilizzando la chiave pubblica.
L’accesso iniziale si può ottenere decriptando la password tramite la chiave privata, sulla console o tramite API.

## Virtual Firewall Protection

AWS consente di gestire il traffico in entrata o uscita dalle istanze tramite i **Security Groups**, sulla base della porta, protocollo e sorgente/destinazione.

Ogni istanza è associata ad _almeno_ un security group, ma ne può avere diversi.

Un security group ha un **“default deny”**, cioè non consente il traffico che non è esplicitamente dichiarato. 

Sorgente e Destinazione possono essere specificate sotto forma di:
- **Security Group**: comprende tutte le istanze incluse in quel security group;
- **CIDR block**: una porzione di rete predefinita;

## The Lifecycle of Instances

### Launching

Esistono diversi servizi addizionali che sono utili quando si lancia una nuova istanza EC2:

- **Bootstrapping**: la possibilità di eseguire codice al momento del lancio di un’istanza (patches, installing, etc.)
- **Instance Metadata**: sono informazioni circa l’istanza che si possono utilizzare per gestire l’istanza stessa. Sono recuperabili tramite chiamata ad API (latest/meta-data) e restituiscono informazioni come:
	- i security group associati;
	- l’instance ID;
	- l’instance type;
	- l’AMI utilizzata in fase di lancio;
  
### Managing Instances

Possibilità di taggare le istanze per un più facile riconoscimento.

### Monitoring Instances

AWS offre il servizio **CloudWatch** per monitoring e alerting.

### Modifying an Instance
Ci sono diversi aspetti che possono essere modificati dopo il lancio:

- **Instance Type**: per adeguare l’istanza al tipo di utilizzo che ne viene fatto, tramite AWS Console, API, CLI. L’istanza deve essere stoppata e poi riavviata dopo il cambio;
- **Security Groups**: possibile gestire i security groups;

### Termination Protection

Quando un’istanza non serve più, lo stato può essere messo a “Terminated”. In questo modo l’istanza viene spenta e rimossa dall’infrastruttura AWS.
Per evitare episodi non propriamente voluti, è possibile abilitare la **Termination Protection** sulle istanze EC2.
In questo modo ogni tentativo di mettere lo stato a “terminated” fallirà.

## Options

E’ possibile configurare diverse opzioni in EC2 per efficientare i costi, gestire la sicurezza e le performance.

### Pricing Options

EC2 è un servizio che si paga per ogni ora in cui un’istanza è attiva. Ci sono però 3 fasce di prezzo che si possono applicare, in base alla modalità con cui si è deciso di lanciare un’istanza:

- **On Demand Instances**: il prezzo pubblicato sul website di AWS si riferisce alle istanze on-demand. E’ il pricing più flessibile che c’è, il cliente sa perfettamente quanto pagherà e può lanciare e terminare istanze a suo piacimento. E’ il meno conveniente dei piani se si guarda ad un consumo orario, ma la sua _flessibilità_ consente agli utenti di risparmiare fornendo risorse di calcolo variabili per _carichi di lavoro imprevedibili_;
-  **Reserved Instances**: consente ai clienti di avere risorse riservate per carichi di lavoro previsti. Rispetto al piano on demand, consente di risparmiare fino al 75% sulla tariffa oraria, ma il cliente deve prenotarne l’utilizzo in anticipo. Ci sono due fattori che determinano il prezzo:
	- **term committment**: cioè la durata della prenotazione (più è grande, maggiore è lo sconto);
	- **le payment options**:
           ▪ **all upfront**: tutto subito;
           ▪ **partial upfront**: una parte subito e poi frazionata mensilmente per la durata della reservation;
            ▪ **no upfront**: tutto mensilmente;
	_Lo sconto applicato è maggiore tanto più è grande la cifra pagata upfront_.
  
	- E’ possibile anche modificare la Reserved Instance e continuare a beneficiare dei 
		benefit della prenotazione. Non può essere fatta relativamente alla durata della 
		prenotazione ma può riguardare:
    	- la modifica della availability zone all’interno della stessa region;
    	- modificare da VPC a EC2-classic;
    	- modificare l’instance type all’interno della stessa family (solo per Linux);

- **Spot Instances**: per carichi di lavoro che non sono time-critical e che possono anche tollerare interruzioni, le istanze Spot sono quelle che garantiscono il _massimo risparmio_. Il cliente sceglie quanto è disposto a pagare per avere un certo tipo di istanza. Quando il prezzo dell’istanza Spot (che dipende dalla domanda e dalla disponibilità di risorse inutilizzate) è al di sotto di quanto ha dichiarato il cliente, allora il cliente riceve l’istanza e inizia a pagare hourly.
	L’istanza rimarrà avviata fino a che:
  	- il cliente la termina;
    - il prezzo supera quanto dichiarato dall’utente;
    - non c’è la necessaria capacità inutilizzata per il carico di lavoro;

### Tenancy Options
Ci sono diverse opzioni per la locazione delle istanze EC2:

- **Shared tenancy**: è la locazione di default per tutte le istanze EC2. Significa che una singola macchina host può ospitare più istanze di customer differenti;
- **Dedicated Instances**: girano su hardware dedicato a un **singolo customer** (tutte le istanze dedicate di uno stesso customer gireranno sulla stessa macchina). Ad ogni modo, le dedicated instances possono condividere hardware con altre istanze dello stesso account AWS che non sono dichiarate come dedicated instances;
- **Dedicated Host**: è un server fisico con capacità completamente dedicata a un singolo customer. Può aiutare nella gestione di costi di licenza;

### Placement Groups

Sono raggruppamenti logici di istanze all’interno di una singola Availability Zone e abilitano le istanza a partecipare a una rete a 10Gbs con bassissima latenza. Ovviamente le istanze devono essere in grado di avere network performance avanzate.

## Instance Stores

Un instance store fornisce uno storage block-level **temporaneo** ad un’istanza.
Questo storage è localizzato nel disco attached all’host. E’ ideale per memorizzazioni temporanee che cambiano di frequente.
La dimensione e il tipo di instance store dipende dal tipo di istanza.
I suoi costi sono inclusi nel costo dell’istanza. Il concetto chiave è che però sono dati temporanei, e vengono **persi** quando:

- si verifica un failure nel driver del disco;
- l’istanza viene stoppata (in caso di reboot invece viene mantenuto);
- l’istanza viene terminata;

## Elastic Block Storage (EBS)

[EBS](/training/aws/ebs)

### References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html

## EC2 Autoscaling

### References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html