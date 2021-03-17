---
title: EBS
description: 
published: true
date: 2021-03-17T16:58:04.987Z
tags: aws, cloud, data persistence, ebs, block storage
editor: markdown
dateCreated: 2021-03-08T12:11:56.140Z
---

# EBS

I volumi EBS sono disponibili di diversi tipi, in base a hardware, performance e costi.

## Magnetic Volumes

I volumi magnetici hanno le caratteristiche meno potenti di tutti i tipi di volumi EBS, e di conseguenza anche il costo minore per GB.
Sono comunque una soluzione eccellente per determinati tipi di carichi di lavoro. Un volume magnetico EBS può avere una dimensione da 1GB a 1TB e garantisce circa 100 IOPS (con la possibilità di avere un burst a centinaia di IOPS). 
Sono consigliati per:

- applicazioni dove l’accesso ai dati non è frequente;
- letture sequenziali;
- situazioni dove uno storage low cost è richiesto;

Sono fatturati mensilmente sulla base della quantità di spazio riservata, al di là di quanta poi è effettivamente utilizzata.

## General purpose SSD

I volumi SSD offrono una soluzione cost-effective utile per la maggior parte dei casi d'uso in quanto offrono ottime prestazioni a prezzo moderato.
E' disponibile in formati da 1GB a 16TB e offre un numero di IOPS base calcolabile come 3 IOPS per GB (es. 1TB: 3000 IOPS).
Al di sotto di 1TB, c’è comunque la possibilità di arrivare a 3000 IOPS (la baseline) per periodi di tempo anche prolungati, tramite il meccanismo dei **crediti**.
Si accumulano crediti durante i periodi in cui non si utilizzano tutte le risorse, che vengono poi utilizzati automaticamente per arrivare a migliorare prestazioni laddove serve.
Anche i volumi SSD vengono fatturati mensilmente sulla base dello spazio riservato. Sono la soluzione migliore per diverse tipologie di scenari come:

- volumi di system boot;
- small-medium databases;
- development e test environment;

## Provisioned IOPS SSD

Sono i volumi progettati per reggere un carico IO intenso e sono anche quelli più costosi.
Un volume IOPS SSD può andare dai 4GB ai 16TB. Oltre alla dimensione, è il cliente che sceglie il numero di IOPS che desidera, fino a un massimo di 30 volte il numero di GB del volume o 20000 IOPS. E’ possibile anche splittare diversi volumi all’interno di una configurazione RAID 0.
Il pricing si basa sulla dimensione del volume e sul numero di IOPS riservati.
Sono i volumi da scegliere in casi di applicazioni come:

- applicazioni critiche che richiedono notevoli performance IOPS;
- grandi database fortemente sotto carico;


## Protecting Data

### Backup/Recovery (Snapshots)

I volumi EBS possono essere soggetti a backup tramite la creazione di **snapshots**. Gli snapshots sono **incrementali**, ossia ogni volta vengono effettuati solo sulle nuove modifiche rispetto ai precedenti. E’ possibile eseguire snapshot in maniera manuale (Console, CLI, API) oppure in modo schedulato.

Gli snapshots vengono memorizzati in Amazon S3 (non del proprio account ma gestito da AWS). L’azione in se non si paga, ma si paga lo storage dello snapshot. Possono essere utilizzati come punto di ripristino solo all’interno della stessa regione in cui sono stati creati. 
Se si ha bisogno di ripristinare un volume in un altra region, va copiato lo snapshot nell’altra region e poi usato come recovery.

In fase di ripristino, il volume viene subito avviato ma i dati vengono trasferiti in modalità **lazy load**, ossia alla prima richiesta di accesso ai dati. E’ _best practice_ inizializzare un volume creato da uno snapshot accedendo a tutti i suoi blocchi in modo da caricare tutti i dati.

### Encryption

Amazon EBS offre supporto nativo all’encryption dei dati, su tutte le tipologie di volume.

Quando si lancia un volume criptato, AWS usa il servizio **KMS** (Key Management Service) per gestire le chiavi di cifratura.

L’encryption è trasparente, l’accesso ai dati rimane lo stesso e le performance sono le stesse (minima latency). Gli snapshot fatti su istanze criptate sono criptati, così come i relativi volumi restored.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html