---
title: Amazon Virtual Private Cloud (VPC)
description: 
published: true
date: 2021-03-19T17:26:44.103Z
tags: aws, cloud, networking, security, vpc
editor: markdown
dateCreated: 2021-03-08T10:04:18.916Z
---

# Amazon Virtual Private Cloud (VPC)

## Amazon VPC

Amazon VPC è il **layer di rete** per Amazon EC2 che consente di costruire delle reti virtuali all’interno di AWS.
E’ possibile controllare vari aspetti di una VPC, compresi il **range di IP addresses**, le **subnets**, configurare le **route tables**, i **network gateways**, e le impostazioni di sicurezza. 
All’interno di una region, è possibile creare diverse VPC: ogni VPC è **logicamente separata** dalle altre.

Quando si crea una VPC si deve specificare il range di indirizzi IPv4 scegliendo un **CIDR (Class Inter Domain Routing)** block, come ad esempio *10.0.0.0/16*.
Il range di indirizzi non può essere modificato una volta che la VPC è stata creata. Come range, le VPC possono andare:

- da un blocco /16 (65,536 indirizzi disponibili) (MAX)
- a un /28 (16 indirizzi disponibili) (MIN)

Gli indirizzi IPv4 di una VPC **non devono sovrapporsi** con quelli di qualsiasi altra VPC con la quale dovrà essere connessa.
Poiché il servizio VPC è stato lanciato dopo il servizio EC2, esistono 2 diverse piattaforme di networking disponibili: 
- EC2-Classic;
- EC2-VPC;

Dal Dicembre 2013 per ogni account AWS EC2 viene creata una **VPC di default** per ogni region, con una **subnet di default** creata in ogni Availability Zone. 
Il blocco CIDR assegnato alla VPC di default è 172.31.0.0/16.

Una VPC consiste delle seguenti componenti:
- **Subnets**;
- **Route tables**;
- **DHCP**;
- **Security groups**;
- **ACLs**;

Ad una VPC possono essere aggiunti **opzionalmente** i seguenti componenti:
- Internet Gateways (IGWs);
- Elastic IP (EIP) addresses;
- Elastic Network Interfaces (ENIs);
- Endpoints;
- Peering;
- Network Address Translation instances and gateways;
- Virtual Private Gateway (VPG)
- Customer Gateways (CGWs);
- Virtual Private Networks (VPNs);

## Subnets

Una subnet è un segmento di una VPC in cui è possibile lanciare istanze EC2, RDS e altre risorse AWS.

Le subnet sono definite dai **CIDR blocks** (es.: 10.0.1.0/24 e 192.168.0.0/24). La subnet più piccola che è possibile creare è una /28 (16 IP addresses). 
AWS **si riserva** per scopi interni 5 indirizzi IP per ogni blocco.

Dopo aver creato una VPC, è possibile aggiungere una o più subnets in ogni Availability Zone. Una subnet **risiede sempre all’interno di una Availability Zone** e non può espandersi tra più zone. Una subnet quindi appartiene sempre ad una sola Availability Zone. 
Ovviamente, possono esserci diverse subnet all’interno di una AZ.

Le subnet possono essere classificate come:
- **Pubbliche**: la route table associata dirige il traffico della subnet verso l’IGW della VPC; 
- **Private**: la route table associata NON dirige il traffico della subnet verso l’IGW della VPC;
- **VPN-only**: la route table associata dirige il traffico della subnet verso il VPG della VPC e non esistono rotte verso l’IGW;

Indipendentemente dalla tipologia, gli indirizzi IP di una subnet **sono sempre privati**.
La VPC di default contiene una subnet pubblica in ogni Availability Zone di ogni singola region, con una netmask di /20.

## Route Tables

Una route table è un costrutto logico all’interno di una VPC che contiene un insieme di **regole (routes)** che vengono applicate alla subnet per determinare come il traffico di rete viene rediretto.

Le rotte consentono alle istanze EC2 di diverse subnet all’interno di una VPC di comunicare una con l’altra. E’ possibile modificare le route tables e aggiungere ulteriori regole.

Ogni route table contiene una rotta di default chiamata **“local”** che abilita la **comunicazione all’interno della VPC**, e questa rotta non può essere modificata o rimossa.

Da ricordare:
- una VPC ha un **router implicito**;
- una VPC in **automatico fornisce una route table** (main) che è possibile modificare;
- è possibile creare ulteriori route tables per una VPC;
- ogni subnet ha la **propria** route table. Se non si specifica una route table specifica, AWS gli **associa la main table della VPC**;
- è possibile **sostituire** la main route table con una custom in modo che in automatico venga associata ad ogni nuova subnet;
- ogni rotta in una table specifica una destinazione CIDR e un target. Per esempio, il traffico destinato verso 172.16.0.0/12 è diretto verso il VPG;

## Internet Gateways

Un **Internet Gateway (IGW)** è un componente opzionale che consente la comunicazione tra istanze all’interno di una VPC e Internet. Un IGW è quindi un target all’interno di una VPC verso il quale **instradare tutto il traffico diretto verso Internet**. 

Si occupa dell’**address translation** per le istanze alle quali è stato assegnato un IP pubblico.

Le istanze EC2 all’interno di una VPC conoscono solo il loro indirizzo privato. Quando il traffico viene inviato da un’istanza verso Internet, l’ IGW traduce l’indirizzo di risposta nell’indirizzo pubblico dell’istanza (o EIP) e **mantiene il mapping tra indirizzo privato e indirizzo pubblico**.

Quando quindi viene ricevuto traffico per quell’ istanza, IGW traduce l’indirizzo destinazione nell’indirizzo privato dell’istanza e inoltra verso l’istanza il traffico.

Per creare un IGW si deve:
1. Associare un IGW alla VPC;
2. Creare una subnet route table per inviare tutto il traffico non locale (0.0.0.0/0) verso l’IGW;
3. Configurare eventuali ACLs e security group per consentire solo il traffico desiderato da e verso la rete;
4. Assegnare un IP pubblico (o un EIP) all’istanza che deve comunicare con l’esterno;

## Dynamic Host Configuration Protocol (DHCP) Option Sets

**DHCP** offre uno standard per passare informazioni sugli hosts in una rete TCP/IP.

AWS in automatico **crea e associa un DHCP ad una VPC** quando essa viene creata e setta le due seguenti opzioni:
- domain-name-servers (defaulted to AmazonProvidedDNS)
- domain-name (defaulted to the domain name for your region)

**AmazonProvidedDNS** è un DNS server di AWS che abilita il DNS per le istanze che devono comunicare tramite IGW.

## Elastic IP Addresses (EIPs)

AWS conserva un **pool di indirizzi IP pubblici** in ogni regione e li rende disponibili per essere associati alle risorse all’interno di una VPC.

Un **Elastic IP address (EIP)** è un **indirizzo IP statico e pubblico** che può essere associato e rilasciato. Consente di mantenere un set fisso di IP addresses nonostante l’infrastruttura sottostante possa variare.

Da ricordare:
- prima di associare un EIP ad un’istanza esso va creato;
- EIPs sono specifici di una regione (_non possono essere assegnati ad istanze in regioni diverse da quella dove è stato creato_);
- C’è una relazione _one-to-one_ tra **network interface e EIP**;
- E’ possibile muovere un EIP da un’istanza ad un’altra, anche tra diverse VPC ma purché siano all’interno della stessa regione;
- EIP rimane associato **fino a che non viene esplicitamente rilasciato**;
- EIP **hanno un costo** quando sono associati ad un’istanza _non attiva_;

## Elastic Network Interfaces (ENIs)

Un **ENI** è una **interfaccia di rete virtuale** che può essere collegata ad una subnet di una VPC.
Può avere **un solo indirizzo IP pubblico** e diversi indirizzi privati, uno dei quali è il cosiddetto **primario**.

Consentono di creare una rete gestita, di utilizzare strumenti di networking e sicurezza nella VPC, creare istanze dual-homed, etc.

## Endpoints

Un Amazon VPC Endpoint consente di creare una connessione privata tra la VPC e altri servizi AWS **senza passare da Internet** e quindi senza richiedere una NAT instance, una VPN, etc.

E’ possibile creare **endpoint multipli** anche per lo stesso servizio, ed è possibile definire nelle route table regole ad hoc in modo da **raggiungere lo stesso servizio in modo diverso in base al mittente**, per gestire policy di accesso diverse.


Per creare un VPC endpoint:
- Specificare la VPC;
- Specificare il servizio (```com.amazonaws.region.service```);
- Specificare la policy (allow full access o creare una custom policy);
- Specificare la route table (una route verrà aggiunta sulla route table specificata);

Esempio:

```10.0.0.0/16 - Local``` → traffico locale
```0.0.0.0/0 - igw-1a2b3c4d``` → traffico verso internet
```pl-1a2b3c4d - vpce-11bb22cc``` → traffico destinato all’ S3 della region inoltrato verso l’endpoint VPC (tutto il resto, compreso il traffico verso S3 in altre regioni, va verso internet)

## Peering

Una **VPC Peering connection** è una connessione di rete tra due Amazon VPC che abilita la comunicazione tra istanze situate su diverse VPC.
E’ possibile creare connessioni tra due VPC dello stesso account, o di altri account. L’importante è che siano all’interno della stessa regione.

Vengono create tramite protocollo request/access: l’owner della richiedente invia una richiesta di peering connection all’owner destinazione, che ha 1 week per accettarla prima che scada.
Una VPC può avere diverse peering connection, ma il peering è una relazione one-to-one tra VPC. Questo vuol dire che:
    • due VPC non possono avere due peering connection tra di loro;
    • le peering connection non sono transitive;
Da ricordare:
    • non è possibile creare una peering connection tra Amazon VPC che hanno blocchi CIDR sovrapposti o corrispondenti;
    • non è possibile creare peering connection tra VPC in diverse regioni;

## References
- https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html