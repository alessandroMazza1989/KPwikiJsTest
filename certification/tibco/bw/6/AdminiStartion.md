---
title: Administration
description: 
published: true
date: 2021-06-07T12:53:43.331Z
tags: 
editor: markdown
dateCreated: 2021-06-07T10:51:33.802Z
---

# Bwagent
## Quali sono le opzioni al comando bwagent. (Choose 3)
Risposta: stop, apiserver, startagent
## Due applicazioni deployate su due macchine M1, M2 sullo stesso appspace.App1 è configurata con activation mode in single node e l'App2 è configurata in multiple appnode. Se casca l'agent2 che succede alle applicazioni?
Risposta: stopped su tutte i due nodi perchè non viene menzionato che le applications erano running.
## Come abilitare l'Authentication per la REST API di un bwagent. Quale file viene modificato e quali formati di password sono utilizzate.

Risposta mia: bwagent.tra e OBF, MD5 or CRYPT
## Riguardo la Securing the bwagent REST API. La domanda chiedeva le modalità di crittografia e in quale file vengono definiti.
Risposta mia: bwagent.tra e OBF, MD5 or CRYPT
Risposta: Bwagent.ini  e  OBF, MD5 or CRYPT
Nel BWAgent.tra uncomment questa line:
java.property.java.security.auth.login.config=%BW_HOME%/config/jaas.login.conf
jaas.login.conf chiama il config/realm.properties che è il file di property di default.
Posso cambiare qua user e password
Posso criptare la password con java in BW_HOME/system/lib/tea java -cp jetty-util-8.1....jar org.eclipse.jetty.util.security.Password admin admin
La password mi viene restituita criptata in 3 modi diversi OBF, MD5, CRYPT
## When configuring bwagents, which two options are available for setting the persistence and the transport provider? (Choose two.)
Risposta: Activespaces, DBEMS

## When configuring bwagents, which two options are available for setting the persistence and the transport provider? (Choose two.)
 
**ActiveSpaces**
EMS
**DBEMS**
TCP
NFS

## As a network administrator, you want to create an agent network so that bwagents can communicate with across multiple computers.What are the two technology types that allow to achieve this goal? (Choose two.)

Database with Tibco Rendezvous
Apache Cassandra with TIBCO Enterprise Message Service
Database with TIBCO FTL
**TIBCO ActiveSpaces**
**Database with TIBCO Enterprise Message Service**

## Domanda su entità che gestisce lo scambio di informazioni tra appnode

## Se sono presenti 5 Bwagents nel TEA, quanti devono essere registered?
Risposta: 1
## Numero minimo di agent settati come server : 
io ho messo 1
## If there are five agents in an agent network, and they have to be managed through a TIBCO Enterprise Administrator Server, how many of them must be registered?
2
**1**   (correct answer)
5
3
## Quali sono le bwagent properties for multi-Agent, Multi-machine Environments?
Risposta: bw.agent.technology.as.role, bw.agent.technology.as.listenURL, bw.agent.technology.as.discoveryURL
## At a minimum, which two properties of a bwagent must be configured for a multi-agent., multi-machine environment that uses TIBCO ActiveSpaces for persistence and transport? (Choose three)
bw.agent.technology.as.remoteDiscoveryURL
bw.agent.technology.as.clientURL
**bw.agent.technology.as.discoveryURL**
**bw.agent.technology.as.listenURL**
bw.agent.technology.as.server
**bw.agent.technology.as.role**

## Which Statement is true when setting up a multi-agent, multi-machine environment using Tibco Active Matrix technology type for a simple server configuration ?

**There as to be at least one server in the bwagent network**
There as to be at least one server and a remote client
There as to be at least two clients in the bwagent network
There as to be at least two server in the bwagent network


## You are using machines in multiple environments. They have Tibco Active Matrix Business Works installed and are in the same IP subnet. You need to ensure that the machines from one environment are not able to connect to another environment. You must achieve this goal without using additional network technology.
 
Ensure that all agents that belong to an environment have the same agent name
Ensure that all machines that belong to an environment have the same machine name
**Ensure that all agents that belong to an environment have the same network name**
Ensure that all machines that belong to an environment have the same network name

Nota: Tutti gli agent dello stesso ambiente devono avere la stessa bw agent network. Crei due bw agent network, uno per ogni ambiente.
## Macchine di due ambienti diversi (Esempio Produzione/collaudo) su stessa ip subnet, come faccio ad isolare i due ambienti senza intervenire sulla rete?
Risposta: Tutti gli agent dello stesso ambiente devono avere la stessa bw agent network. Crei due bw agent network, uno per ogni ambiente.
## Which runtime entity is required to run in an enterprise mode using the default domain data storage?

DataBase Server
**bwagent**
bwdesign
Tibco Enterprise Message Service

○	Seconda Domanda. Quale entità runtime viene utilizzata per creare runtime entity in ambiente enterprise?

Risposta: bwadmin
## As a network administrator, you are told to create an agent network and provide access via REST for managing the TIBCO AM BW applications, AppNodes, and AppSpaces. This URL should be accesible from other machines. How will you configure the bwagent?
Start the bwagent with the apiserver option, and configure the hostname in bwagent.xml
**Start the bwagent with the apiserver option, and configure the hostname in bwagent.ini**
Start the bwagent with the apiserver option, and configure the hostname in bwagent.tra
Start the bwagent with the apiserver option, and configure the hostname in config.ini

## You need to perform a Remote Deployment from BuisnessStudio by using the Deployment Servers view. Which utility do you need to have running in order to archive this?
bwadmin
bwinstall
**bwagent**
bwdesgin
## The Tibco Enterprise Administrator as multiple components, such as the server, the agent, and the server UI. Which communication mechanism do the server and the agent component use to talk to each other?
Shared file system
Tibco Enterprise Message Service
Tibco Rendezvous
**Rest API**

## Which two roles are available for bwagent while using ActiveSpaces for data persistence?  (Choose two)

a. Seeder
b. Manager
c. **Client**
d. **Server**

## What is the purpose of bwagent?

a. to synch data directly between a machine and local files managed by AppSpaces
b. to synch data directly between a machine without a third component
c. **to synch data directly between a machine and a datastore managed by AppSpaces**
d. to synch data directly between machines in separate admin domains

# Bwadmin

## Comando bwadmin per upload di un archivio su uno specifico path all'interno di un dominio.
Risposta: bwadmin upload -d myDomain -path <relative_path> application.ear
bwadmin upload -d myDomain C:/<path>/application.ear (-replace se esiste gia) in questo modo l'ear viene caricato sulla directory di default BW_HOME/domains/domain_name/archives
## In modalità local chi gestisce le entità a runtime?
Risposta: bwadmin
## Quale entità runtime viene utilizzata per creare runtime entity in ambiente enterprise?
Risposta: bwadmin
## How do you create runtime entities with the deployment mode set to local?
Create the runtime entities while installing the product.
Local mode uses default runtime entities created by the bwagent.
Use TIBCO Enterprise Administrator to create runtime entities.
**Use BwAdmin to create runtime entities**
## You have configured your bwagent to run in enterprise mode. What are the two different utilities that you can use to deploy your application? (chose two)
TIBCO Administrator
bwdesign
bwinstall
**TIBCO Enterprise Administrator**
**bwadmin**
## You have two machines configured in an agent network. A domain and AppSpace span across both machines. Each machine had a single AppNode, which is part of the same AppSpace. Which utility allows you to deploy an application to the AppSpace so that it runs on each AppNode?
bwinstall
bwdesign
bwdesign
**bwadmin**
## Which three statements are true about bwadmin backup and restore commands in an enterprise mode? (choose three) 
**The backup command exports the current state of the environment to a command file.**
The bwadmin backup command and the bwadmin restore command are complementary.
**The restore command restores the file system of a bwagent to the state of the persistent datastore.**
**The bwadmin backup command and the bwadmin restore commad are not complementary.**
The backup command exports the current state of the environment to a datastore.
The restore command restores the file system of a bwagent to the least checkpoint state of a datastore.

## Which three tasks can be performed using bwadmin tool? (Choose three)

a. Validating the workspace
b. **Deployng and managing applications**
c. Generating EAR file
d. **Creating runtime entities**
e. **Addressing different bwagent networks**

# Bwdesign

## Which two functions can be performed using the bwdesign tool? (Choose two)

a. **Validate modules**
b. **Import ZIP file into workspace**
c. Upload an archive to a domain
d. Deploy an application

# Appspace / Appnode / Domain / Server
## Cosa è un'appsapce
Risposta: non è un contenitore fisico
AppNodes. An AppNode is a JVM process that hosts applications created in TIBCO Business Studio. An AppNode can belong to only one AppSpace. Each application that is deployed into a AppSpace runs on all of its AppNodes. AppNodes allow vertical and horizontal scaling.
E’ un’entità che può avere al proprio interno più contenitori che hostano applicazioni

https://docs.tibco.com/pub/activematrix_businessworks/6.1.0/doc/html/GUID-1E3DEBDB-0D60-4290-A284-09E7329F804B.html

## Quale di queste definizioni è corretta nel caso di Appspace?
Risposta: E’ un’entità che può avere al proprio interno più contenitori che hostano applicazioni
## Due appnode sulla stessa macchina, come configuro rest doc dedicato ad ogni nodo
Risposta: Modifico la property BWRest.docApi nel config.ini del bwappnode
## What does degraded state indicate for an AppSpace?
Risposta: The AppSpace does not have the minimum specified AppNodes.
## What does degraded state indicate for an AppSpace? 

The config file for the AppSpace has incorrect values.
**The AppSpace does not have the minimum specified AppNodes.**
The AppSpace is opened in an earlier version of TIBCO ActiveMatrix BusinessWorks.
The domain was moved from local to enterprise mode.
## Scegliere le affermazioni corrette nel caso di AppNodes (2 scelte)

## Si hanno due Macchine con due Appnode presenti su un Appspace e con attivazione su Single Node. Hai impostato la managed Fault Tollerance. Per errore l’operatore stoppa l’applicazione. Cosa succede?

## An application you have created with activation set to Single AppNode is deployed into an AppSpace consisting of two AppNodes (A1 and A2). One of the administrators accidentally stops AppNode A1. What is the expected behavior of your application?
The application will be activated on A2, but no requests are processed.
The application is standby on A2, and no requests are processed.
The application will be activated on A2, and requests are processed.
**The application is stopped on A2, and no requests are processed.**
## Stessa domanda (vedi precedente) senza managed fault tollerance.

## How do you generate the config file for an AppSpace?
**Run the command: bwadmin config -d myDomain -a myAppspace -cf <temporaryLocation>/config.ini**
Run the command: bwinstall config -d myDomain -a myAppspace -cf <temporaryLocation>/config.ini
Run the command: bwdesign config -d myDomain -a myAppspace -cf <temporaryLocation>/config.ini
Copy the config file from the samples directory

## Cosa indica lo stato out-of-sync sull’appspace?
Risposta da doc: The AppSpace is out of synchronization. The out-of-sync state may occur when:
○	a bwagent is not reachable due to network failure, or
○	the bwagent configuration may not have been applied remotely.
https://docs.tibco.com/pub/activematrix_businessworks/6.5.1/doc/html/GUID-671998A0-FF69-4C1C-9A10-02F1B21AFFE1.html
## What does an out-of-sync status mean after deployng an application to an AppSpace? (Choose Two)

A bwagent configuration failed to start.
**A bwagent is not reachable due to network failure.**
**A bwagent configuration may not have been applied remotely.**
A bwagent is not reachable because the AppNode is stopped.
A bwagent is stopped.

## You need to activate your process on a different AppNode, but only if the existing AppNode fails. Which Activation setting should you use to achive this goal?
Fallover AppNodes
Multiple AppNodes
Elastic AppNodes
**Single AppNode**
## TIBCO Enterprise Administrator cannot find a domain. Whats is the problem? (Da rivedere, Nicola porta in local mode)
The domain was created in local mode.
The domain was created in enterprise mode.
The TIBCO Enterprise Administrator cannot access the local file system.
The TIBCO Enterprise Administrator cannot connect to the database.

## Configurazione single appnode cosa bisogna configurare?
persistent mode group
process activaction

## Which three data elements are included in the TRA file for AppNode? (Choose three)

a. **Path of the JVM**
b. **Classpath**
c. Configuration for data persistence
d. Logging configurations
e. **Memory settings**

## Which property is available only in the config file for appnode?

a. Hawk microagent configuration
b. Swagger configuration
c. Palette properties
d. **Engine settings**

## Which two statements are true about BusinessWorks runtime components? (Choose two)

a. A domain contains exactly one appspace
b. An application can be deployed to a specific appnode in an appspace
c. **When an application is deployed to an appspace, it is deployed to all appnodes in that appspace**
d. **An application is always deployed to an appspace**

## Which three statements are true BusinessWorks 6.x runtime components? (Choose three)

a. **An AppSpace is a logical boundary which contains a collection of AppNodes**
b. **An AppNode is a JVM that runs application as OSGi bundle**
c. An AppNode can run only one application
d. **A Domain is a collection of AppSpaces**

## Which two are choices for creating a domain in Enterprise mode? (Choose two)

a. **TIBCO Enterprise Administrator Web User Interface**
b. Register the bwagent on TEA
c. TIBCO ActiveSpaces
d. **bwadmin command line tool**

## Which file is used to enable HMA for an AppNode?

a. **config.ini**
b. bwagent.ini
c. bwappnode.log
d. bwappnode.tra

Engine

## Which is a true statement about the responsabilities of a BusinessWorks 6.x engine?

a. **It runs an application in an appnode**
b. It is responsible for synchronizing datastore with the local file system
c. It performs administration commands
d. It is responsible for communication with TEA

# Upload / Deploy / Ear
## Appspace con app1 deployata, quale di questi casi è vero?
Risposta: se crei un altro nodo l'applicazione viene deployata automaticamente + se crei un altro nodo aumenti la capacità.
## Which two statements are true about applications deployed to an AppSpace? (choose two)

Adding more appnodes will not affect capacity.
Adding appnodes after an application is deployed does not scale the application.
**Adding more appnodes will increase capacity.**
**A deployed application scales dynamically across all the appspace.**
A deployed application scales dynamically across all the appnode.

## Come si possono creare gli EAR?
Risposta: business Studio e bwdesign
bwdesign utility provides a command line interface for creating, validating, importing or exporting resources stored in a workspace.
bwdesign legge le cose dentro un workspace --> allora per farlo partire faccio:
bwdesign -data C:\myWorkspace.
bwdesign> export -e App.application C:/<path>/outputFolder
## Con quale tool è possibile creare un ear su BW6? scegli 2 risposte

**TIBCO Business Studio**
**bwdesigner**
bwinstall
bwadmin
## Con quale tool è possibile eseguire i deploy degli ear? scegli 2 risposte

**TIBCO Business Studio**
bwdesigner
bwinstall
**bwadmin**

## Which three components can be used to deploy applications in Businessworks 6.x? (Choose three)

a. **bwadmin command line tool**
b. bwagent.ini configuration file
c. bwdesign command line tool
d. **TIBCO Business Studio**
e. **TIBCO Enterprise Administrator**
## Hai un’applicazione che deve funzionare sia su sistema Windows che su sistema Linux dovendo considerare una path legata ai file system. Quale metodo bisogna usare?
Risposta: Profile application
## A Tibco AM BW application will be deployed on both Windows And Linux Servers; the application uses a property named Path that uses the appropriate operating system syntax to point the files in the file system. How can you specify different configuration of the variables that the application uses?
by using a variable insted of a Property
**by creating different Application Profiles**
by defining the path property ad a Process Property
by creating different Application Module Profiles
## Cosa serve in una configurazione Simple Server Configuration?
Risposta: Almeno un bwagent con role server
Simple High Availability Configuration: è quella con piu di un server (che gestiscono il datastore)
High Availability Configuration with Remote Clients: Come prima ma permette ma the TCP connection mesh can be avoided by setting the bwagent

## Domanda riferita a Simple Server Configuration simile alla domanda precedente
Risposta: Almeno un Role Server

## What is the appropriate command line option to use when uploading Tibco BusinessWorks Application to a non- …archive location named QA

bwadmin  upload archive/QA application.ear –d MyDomain
bwadmin  upload –d MyDomain archive/QA application.ear
bwadmin  upload –path archives/QA application.ear –d MyDomain
**bwadmin  upload –d MyDomain –path /QA application.ear**
 
## Which three TIBCO AM BW artifacts can be designed using TIBCO Business Studio? (Choose Three)

bwagent network
**applications**
AppNode
**application module**
**shared module**
domain
## Quando un’applicazione mostra lo stato "impaired" durante lo startup?

An application having an impaired status means that it is not ready to run.

## Why does an application show "impaired" state during startup?

a. Multiple applications are trying to startup at the same time
b. **All dependencies are not available**
c. bwagent is not available
d. Connection with TEA is not available
## What are the three minimum requirements for deploying  TIBCO Active Matrix BusinessWorks Applications across multiple machines? (Choose three)
Set up a domain with an AppSpace and an AppNode
Set up the deployment mode to enterprise by using the bwagent utility
**Set up a domain with at least one AppSpace and two AppNodes**
**Set up the deployment mode mode to enterprise by using the bwadmin utility**
**Set up the persistence store and communication transport layer for domain configuration data**
Set up a domain with deployment mode set to file system

# Persistence modes

## What are the three options available to define the engine persistence mode at an AppSpace level? (Choose three.)
Risposta: memory, datastore, group
## What are the three options available to define the engine persistence mode at an AppSpace level? (Choose three.)
 
**memory**
cache
**datastore**
file
**group**
exclusive
## Quali sono le tre opzioni per settare la persistenza dell'engine
Risposta: group, datastore e memory
## Cosa è obbligatorio nel caso in cui la persistence mode property è impostata su group?
Risposta: ems as group provider technology
## Se la modalità è group che vuole dire?
Risposta: Appspace è configurato in modalità managed fault tollerance
## La differenza tra managed e non-managed fault tollerance
Risposta: nella managed gli appnode sono a conoscenza uno dell'altro e un appnode può recuperare il lavoro di un altro appnode caduto.
https://docs.tibco.com/pub/activematrix_businessworks/6.2.2/doc/html/GUID-8361DA81-4AA8-45EA-A98A-1624FEC6BF54.html
Uno lo setto con persistence=group e l’altro con datastore. Entrambe gestiscono checkpoint.
## Your company requests that you set up managed fault tolerance for applications deployed on AppSpace A1. How should you configure the engine persistence modes and requirements in order to fulfill the request?
Risposta: Engine persistence mode must be set to group + EMS + Database
## Your company requests that you set up managed fault tolerance for applications deployed on AppSpace A1. How should you configure the engine persistence modes and requirements in order to fulfill the request?
Risposta: Engine persistence mode must be set to group, TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them, and a database is required for persistence.

## Your company requests that you set up managed fault tolerance for applications deployed on AppSpace A1. How should you configure the engine persistence modes and requirements in order to fulfill the request?
 
A.Engine persistence mode must be set to memory, and TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them.
B.Engine persistence mode must be set to datastore, and TIBCO ActiveSpaces must be configured to let AppNodes communicate between them.
C.**Engine persistence mode must be set to group, TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them, and a database is required for persistence.**
D.Engine persistence mode must be set to TIBCO ActiveSpaces, TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them, and a database is required for persistence.
## Fault tolerance (3 o 4 domande): Differenze tra managed e non managed.come impostare la persistence mode nei due casi. 4 scenari in cui era richiesto quale delle due modalità scegliere.
Risposta: Appnode sanno o no della presenza di altri appnode
## Which two engine persistence modes allow the use of checkpoints? (Choose two)
Risposta: Datastore e Group
## Which two engine persistence modes allow the use of checkpoints? (Choose two)

a. Filesystem**
b. **Datastore
c. **Group**
d. Memory
R: b,c
## Quando la persistence mode property è impostata su group, quale di queste risposte è corretta?
database connection deve essere specificata solo a livello di appspace
## Which to statements are true about a bw.engine.persistenceMode that is set to group? (Choose 2 answers)
The non-managed fault tolerance feature requires this properties
The database connection configuration must be specified only at the AppNode level
The engine does not require a database to be configured
**The engine required a group provider such as Tibco Enterprise Message Service to be configured**
**The group mode supports the Checkpoint activity and other persistence features**

## What is indicated if the engine persistence mode (bw.engine.persistenceMode) is set to type group?
**ActiveMatrix BusinessWorks Environment is in managed fault tolerance mode**
The engines are unaware of the existence of each other
Each AppNode in a AppSpace has a unique database specified at the AppNode level
ActiveMatrix BusinessWorks Environment is in non-managed fault tolerance mode

## Quale definizione è corretta per managed fault tollerance e non-managed fault tollerance? (scegliere due )
Risposta: studiare bene Fault Tollerance – vengono mostrati vari casi
## You have a TIBCO ActiveMatrix BW application running on multiple AppNodes, which are part of the same AppSpace. You want to read or update the module shared variable state. Which option should you select?
bw.engine.persistenceMode = “AppSpace”
**bw.engine.persistenceMode = “group”**
bw.engine.persistenceMode = “datastore”
bw.engine.persistenceMode = “true”

## The TIBCO AM BW architect requests the application developer to desgin applications that allow high availability. Which three configuration properties should be set so that managed fault tollerance is implemented? (Choose three)
bw.engine.persistenceMode=datastore
a minimum of two AppNodes across two AppSpaces
**Process Activation In Business Studio**
**bw.engine.persistenceMode=group**
Process Mode in Business Studio
**a minimum of two AppNodes in an AppSpace**

## Which two statements are true about the fault tolerance feature of TIBCO AM BW applications? (Choose two)

Managed fault tolerance requires persistence mode to be set memory, while non-managed fault tolerance requires persistence mode to be set to group.
Managed fault tolerance requires activation mode to be set to Single AppNode, while non-managed fault tolerance requires activation mode to be set to Multiple AppNode.
**In Managed fault tolerance, AppNode are aware of other AppNodes in the AppSpace, while in non-managed fault tolerance, AppNodes are unaware of other AppNodes in the AppSpace.**
**Managed fault tolerance requires persitance mode to be set to group, while non-managed fault tolerance requires persistence mode to be set to datastore.**
Managed fault tolerance supports checkpointing, while non-managed fault tolerance does not support checkpointing.

## Domande sulla fault tolerance (managed fault tolerance / non -managed fault tolerance) : differenze tra i due tipi di fault tolerance gestiti, quali sono gli engine persistence mode che vanno settati per le diverse tolerance gestite, esempi di environment con descrizioni di configurazioni, e domande di cosa succede alle applicazioni se una macchina va giù...

➢	Managed Fault Tolerance

In managed fault tolerance, when an AppNode fails, the application on another AppNode takes over automatically. The AppNodes in an AppSpace are aware of each other’s existence and the engines collaborate to provide fault tolerance.The managed fault tolerance requires:

○	 The engine persistence mode (bw.engine.persistenceMode) to be set to type group. The persistence mode of type group requires both database and group provider configurations. See Engine Persistence Modes for details.(Memory,Datastore,Group)
○	  A minimum of two AppNodes in an AppSpace.
Sorgente: https://docs.tibco.com/pub/activematrix_businessworks/6.2.2/doc/html/GUID-8361DA81-4AA8-45EA-A98A-1624FEC6BF54.html

➢	Non-managed Fault Tolerance

In non-managed fault tolerance, the AppNodes in an AppSpace are not aware of each other's existence and there is no collaboration between the engines. Consequently, if an AppNode fails, then another AppNode in the AppSpace will not take over automatically.The non-managed fault tolerance requires:
○	The engine persistence mode (bw.engine.persistenceMode) to be set to type datastore. The persistence mode of type datastore requires database configurations. See Engine Persistence Modes for details.
○	 If there are multiple AppNodes in the AppSpace, then each AppNode must be configured with a unique database configuration. An AppNode specific database configuration is stated through the AppNode config.ini file.

## A company has a requirement that during failover, new jobs and all check-pointed jobs should be processed. Why is managed fault tolerance the best configuration option?
Because it is easier to configure then non-managed fault tolerance and requires no design time setup.
**Because the appnode are aware of each other, and the engines collaborate to provide fault tolerance.**
Because it requires only one AppNode to be deployed for engines to collaborate and provide fault tolerance.
Because each AppNode must be configured with a unique database configuration and collaboration between engines.

## Which action provide environment fault tolerance?

a. Setting activation mode to Multiple AppNodes
b. Setting engine persistence mode as memory
c. **Configuring multiple bwagents as server in the network**
d. Setting activation mode to Single Node

# Drivers / Installation

## Qual è la procedura per installare in un ambiente di runtime i driver Oracle JDBC?
Risposta: Copiare il file nella cartella di terze parti JDBC + utilizzare bwinstall oracle-driver
## Which two actions must be performed for an Oracle driver to be used inside BusinessWorks environment? (Choose two.)

**Use the bwinstall utility**
Copy the JDBC jar file to any folder in the RunTime Classpath
**Copy the JDBC jar file to the Tibco third-party JDBC Driver folder**
Use the bwadmin utility
Copy the JDBC jar file in the bwagent lib folder
## Quali sono i DB per cui è necessario fare l’installazione dal bwinstall?
Risposta: ci sono gia i driver per PostgreSQL e Microsoft SQL Server, gli altri bisogna fare la procedura.
## Quali driver JDBC non sono installati?
Risposta: le opzioni sono 5 e sono presenti Postgres, MySQL e MicrosoftSQL
## Which to database driver require additional configuration in other to be used with Tibco Active Matrix BW? (Choose two.)

HSQLDB driver
**MySQL Database driver**
**Oracle Database driver**
Microsoft SQL Server driver
Postgress SQL driver

## Driver DB supportati di default e per i quali non  vanno installati i driver sulle macchine in fase di configurazione degli agents (choose 2)

Oracle
**Microsoft SQL**
**PostgreeSQL**
MySQL

## Which statement is true about BusinessWorks 6.x installation?

a. TEA must be installed on all the machines where BW is running
b. BusinessWorks 5 and 6 cannot co-exist in the same TIBCO HOME
c. **There is no dependency between BW and TEA for order installation**
d. TIBCO Enteprise Administrator must be installed after BusinessWorks

# Remote client

## Requisiti minimi per configurare remote client su appspace (activespace)
Risposta: Nel bwagent.ini bisogna settare i seguenti parametri: role=server, remote-discoveryURL e remoteListenURL
## RemoteCLientConfiguration

Risposta: bw.agent.technology.as.remoteListenURL e bw.agent.technology.as.remoteDiscoveryURL
Nel bwagent.ini bisogna settare i seguenti parametri: role=server, remote-discoveryURL e remoteListenURL

## M1 M2 M3 con M3 remote client
Risposte: settare
M1 role=server remoteListenURL=tcp://Machine1:5060 remotediscoveryURL=tcp://Machine1:5050;Machine2:5050 to
M2 role=server remoteListenURL=tcp://Machine2:5060 remoteDiscoveryURL=tcp://Machine1:5060;Machine2:5060
M3 role=remoteclient remoteDiscoveryURL=tcp://Machine1:5060;Machine2:5060 (remoteListenURL M1;M2)
## Scenario: sulla macchina M1 e M2 sono configurati con role=server i 2 bwagent, su M3 è configurato il bwagent con client. Qual è la corretta configurazione per gestire M3 come remote client?
Risposta: impostare il remoteListenUrl su M1 e M2 e il remoteDiscoveryURL su M3=remoteListenURL M1;M2    
## TIBCO ActiveMatrix BusinessWorks agents on machines M1, M2, and M3 are configurated with TIBCO ActiveSpaces as the persistence and transport technology. M1 and M2 are configured ad servers. Assume all agentes are started on port 5060. For M3 to act as a remote client, which property should you set on all agents so that M3 would remain unaffected if mahine M1 goes down?

remoteListenURL on M1 and M3; remoteDiscoveryURL on M2
remoteDiscoveryURL on M1 and M3; remoteListenURL on M2
remoteDiscoveryURL on M1 and M2; remoteListenURL on M3
**remoteListenURL on M1 and M2; remoteDiscoveryURL on M3**
 in aggiunta M3 role=remoteclient remoteDiscoveryURL=tcp://Machine1:5060;Machine2:5060 (remoteListenURL M1;M2) ….M3 discoveryUrl

# TEA
## Quale feature usi per modificare un puntamento a ems/jdbc da TEA a runtime:
Risposta: Module properties
## Cosa utilizzi per modificare un’impostazione sul TEA durante il running di un’applicazione?
Risposta: Module Properties
## Cosa utilizzi per modificare un’impostazione sul TEA durante il running di un’applicazione?

Risposta: Application Properties

## A Tibco ActiveMatrix BusinessWorks application connects to a database and the Tibco EMS instance. On deployment, a system administrator has to replace the connection parameters to the production database and EMS instance. Which type of properties can be used from the Tibco Enterprise Administrator solution to modify this connection’s parameters?
Module Properties
**Application Properties**
Process Properties
Global Variable
## Come comunica il TEA con il bwagent
Risposta: REST API
## Come comunica il TEA bwagent TEA agent port.

9091 
sorgente:
https://docs.tibco.com/pub/activematrix_businessworks/6.1.1/doc/html/GUID-153131AE-741F-44BC-A959-60573CF17F29.html

## TEA communicates with bwagent through which port?

a. 5555
b. 8079
c. 8777
d. **9091**
## Come comunica il tea con i sistemi esterni? Non trovata sulle domanda a disposizione
 redezvous
 ems

## Which two attributes are provided to TEA by prouct agent? (Choose two)

a. Load balancing feature
b. **Display details**
c. Fault tolerance feature
d. **All product data**

## Which three statements are true for TIBCO Enterprise Administrator? (Choose three)

a. **It manages Domains/AppSpaces/AppNodes across the machines**
b. **It provides web-based GUI and command-based shell interface**
c. It provides peer-to-peer administration
d. **It is based on agent-based architecture**

