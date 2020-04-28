---
title: Common Topics
description: Indice degli argomenti comuni
published: true
date: 2020-04-28T11:00:42.883Z
tags: commons, software versioning, git, networking, pattern, design, web services, unix, shell, wsdl, soap, rest, server, algoritmi, databases, sql, relational, lifecycle, log
---

In questa sezione verranno trattati i principali argomenti che rappresentano la base di una formazione specialistica.
Individuare le sezioni di interesse insieme al proprio tutor.
<p>&nbsp;</p>

# Databases
### Basic
- **Obiettivi**
   1. RDBMS: definition 
   2. Table: definition 
   3. Primary key (PK): definition and usage
   4. Foreign key (FK): definition and usage 
   5. How to define relationships between tables
   6. SQL (Standard Query Language) definition 
   7. SQL Syntax.
   8. Fundamental keywords (SELECT, INSERT, UPDATE, DELETE)
   9. Filter the selected records (WHERE clause)
   10. Comparison operators ( =,<, >, !=, <>, LIKE)
   11. record in list (IN clause)
   12. Sorting records (ORDER BY clause)
   13. Aliasing 
   14. SQL joins (Inner, Outer, Left, Right, Full, Cross)
   15. Aggregation functions, GROUP BY clause 
   16. Create DB
   17. Create Table 
   18. Constrains 
- **Link Utili**
[w3school SQL reference](http://www.w3schools.com/sql/default.asp)
[html.it guida al linguaggio SQL](http://www.html.it/guide/guida-linguaggio-sql/)
[Postgress exercises site](https://pgexercises.com/) 
- **Tools & Lab**
Tool [PostgreSQL](http://www.postgresql.org/download/)
Lab [KP drive SQL exercises](https://drive.google.com/open?id=0BydghG4Au4Hfd1E0b3pQQlhvNk0)

### Advanced
- **Obiettivi**
   1. Create Index
   2. Drop
   3. Alter
   4. Auto Increment
   5. Views
   6. DATE functions 
   7. CASTING functions
   8. The NULL value
   9. NULL functions
   10. DATA types (RDBS dependant)

# XML/XSD/XPATH/XSLT
## XML
- **Obiettivi**
  1. XML:Definition
  2. Use cases 
  3. hierarchical structure of an XML 
  4. Sintax
  5. XML tags 
  6. XML attributes
  7. Namespaces
  8. Encoding
  9. XML Doctypes
  10. XML Schema (XSD): Definition
- **Link Utili**
[w3School XML Reference](http://www.w3schools.com/xml/)
- **Tools & Lab**
Tool [Online XML - XSD formatter](http://www.freeformatter.com/)

## XSD
- **Obiettivi**
1. XML Schema document: definition
2. Why using an XSD document
3. How to reference a XSD document from within a XML document
4. &lt;xs:schema> tag's attributes
5. Simple types 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Elements
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Attributes
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Constrains
6. Complex Types 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Elements
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Empty elements
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Types with only elements 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Types with only text
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Indicators (choice, sequence, all)
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. &lt;any> e &lt;anyAttribute> tags 
- **Link Utili**
[w3School XSD Schema Reference](https://www.w3schools.com/xml/schema_intro.asp)
- **Tools & Lab**
[Tool: Online XML - XSD formatter](http://www.freeformatter.com/)
[**Lab**: KP xsd exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfaEJXMktIQW5ROFE)

## XPATH
- **Obiettivi**
1. XPath Terminology  (Nodes, Atomic values, Items)
2. Relationships between the nodes (Parent, Children, Sibling, Ancestors, Descendants)
3. XPath Syntax 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Selecting nodes 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Predicates
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Wildcards 
4. XPath Axes concept
5. XPath operators 
- **Link Utili**
[W3 school Xpath reference](https://www.w3schools.com/xml/xpath_intro.asp)
- **Tools & Lab**
[Tool: Online XML - XSD formatter XPath tester](http://www.freeformatter.com/xpath-tester.html)
[**Lab**: KP Xpath exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfRG5iN0ctV0VLbXM)

## XSLT
- **Obiettivi**
1. XSLT document definition
2. &lt;stylesheet> and &lt;transform> elements
3. &lt;template> element
4. &lt;value-of> element
5. &lt;for-each> element
6. &lt;sort> element
7. &lt;if> element
8. &lt;choose> element
9. &lt;apply-templates> element
- **Link Utili**
[W3 school Xsl reference](https://www.w3schools.com/xml/xsl_intro.asp)
- **Tools & Lab**
[Tool: Online XML - XSD formatter xsl tranformer](http://www.freeformatter.com/xsl-transformer.html)
[**Lab**: KP Xsl exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfWkpkNk1wTmNlRkE)

# Unix Shell
Intro
### Basic
- **Obiettivi**
1. What is unix
2. Files and processes
3. Unix file system, directories
4. Unix shell/command line 
5. List files and directories (ls)
6. Create directories (mkdir)
7. Change directory (cd)
8. The . and .. directories
9. Show current directory (pwd)
10. Copy a file or directory (cp)
11. Move a file or directory (mv)
12. Remove file or directory (rm)
13. Show the content of a text file (less, cat, head, more, tail)
14. Navigate or search inside the content of a file (more, grep, less,)
15. wc command
16. Rerouting (output, input, pipes)
17. Wildcards (*)
18. Modify the permissions on a file (chmod)
19. Show the list of the processes (ps)
20. Start processes in background ( nohup , & )
21. Kill/Terminate a process (kill,  kill -9)
22. Other useful commands
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. netstat (netcat) 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Telnet
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Ping
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Wget
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Curl
24. Finding your own IP 
- **Link Utili**
[Unix guide (required content extends till tutorial number 6)](http://www.ee.surrey.ac.uk/Teaching/Unix/)
- **Tools & Lab**
Tool [Virtual box VM guide and references](https://docs.google.com/document/d/1OSbQtX0NoG31UhdtxFlawpnaja8KeDzXd8wushVZzdk/edit?usp=sharing)
Lab [KP Unix/Linux exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfUzFobUxTU0wtV1E)

### Advanced
- **Obiettivi**
1. Shell scripting
- **Link Utili**
[Unix shell scripting (sections from 1 to 10)](https://www.html.it/guide/shell-scripting-la-guida/)

# Networking
Intro
### Basic
- **Obiettivi**
1.Stack ISO/OSI
2.LAN/WAN/MAN
3.Subnet
4.ridge/NAT
5.ateway
6.Routing table
7.Firewall
- **Link Utili**
Coming soon

### Advanced
- **Obiettivi**
1.Cloud
2.SaaS
3.iPaas
- **Link Utili**
Coming soon

# Software Versioning
Questo capitolo ha l’obiettivo di introdurre il concetto di controllo di versione, di descriverne i diversi approcci e di approfondire gli strumenti maggiormente utilizzati per implementarlo, specialmente nell'ambito dei sistemi software.

Un sistema di controllo di versione (VCS) consente di gestire le modifiche apportate ai file di un progetto (non necessariamente software) su cui tipicamente lavorano più persone. Scopo di un VCS è quello di realizzare una corretta gestione delle modifiche garantendo:

- **Reversibilità**: cioè la capacità di un VCS di poter sempre tornare indietro in un qualsiasi punto della storia del codice sorgente, ad esempio nel caso in cui ci si è accorti di aver introdotto un errore ed è necessario ripristinare l’ultima versione stabile del software;
- **Concorrenza**: cioè la possibilità di consentire a più persone di apportare modifiche allo stesso progetto, facilitando il processo di integrazione di pezzi di codice sviluppati da due o più sviluppatori;
- **Annotazione**: cioè la possibilità di aggiungere spiegazioni e riflessioni ulteriori alle modifiche apportate; in pratica è possibile “allegare” alla modifica effettuata, delle note in cui ad esempio si spiega il motivo per cui è stato necessario fare tali modifiche, eventuali criticità o qualsiasi altra informazione che si pensa possa essere utile a tutto il team di lavoro;

Con queste caratteristiche un VCS risolve uno dei problemi più comuni dello sviluppo del software: il timore di modificarlo. Quante volte si sente dire “se qualcosa funziona, non cambiarla” che può apparire come una frase scherzosa ma che poi spesso nella realtà avviene. Ecco, un sistema di versionamento ci permette di liberarci dalla paura di modificare il codice perchè sappiamo che in caso di problemi possiamo sempre “tornare sui nostri passi”.

I VCS si suddividono in due grandi categorie:
- **Centralizzati**;
- **Distribuiti**;

Un VCS centralizzato (CVCS) è un sistema progettato per avere una singola copia completa del repository, ospitato in uno o più server, dove gli sviluppatori salvano le modifiche che hanno fatto. Avere un VCS che dipende completamente da un server centralizzato ha una conseguenza ovvia: se il server o il collegamento va giù, gli sviluppatori non saranno in grado di salvare le modifiche. O peggio ancora, se il repository centrale viene danneggiato, e non esiste il backup, la storia del nostro progetto andrà perso. Inoltre un CVCS può anche essere più lento in quanto se si fa un qualche modifica in locale questa deve essere registrata sul server centrale e quindi tutta l’operazione è strettamente legata alla velocità di connessione col server centrale.

Nei sistemi distribuiti (DVCS) invece, ogni sviluppatore ha una propria copia locale di tutto il repository e può salvare le modifiche ogni volta che vuole. Anche in questo caso esiste un server remoto che contiene l’intero repository condiviso da tutti gli sviluppatori, ma, se in un certo momento il server che ospita il repository è giù, gli sviluppatori possono continuare a lavorare senza alcun problema, rimandando la registrazione delle modifiche nel repository condiviso in seguito. Inoltre, i DVCS sono molto più veloci, poiché le modifiche sono gestite localmente, e l’accesso al disco è più veloce di un accesso alla rete, almeno in condizioni normali.

**GIT** è un sistema di versionamento distribuito (DVCS) che si contrappone a quelli centralizzati (CVCS), come ad esempio CVS o **SVN**. 

## GIT
### Basic
- **Obiettivi**
	- Conoscere git e le sue basi;
	- Saper installare e configurare git;
	- Saper collegare un repository remoto con il file system locale;
	- Saper modificare un file, committarlo e pusharlo sul repository remoto;
	- Saper scaricare un file aggiornato remotamente;
	- Saper creare un branch;
	- Saper modificare un branch;
	- Saper mergiare un branch nel repository master e risolvere eventuali conflitti;
  
- **Link Utili**
[Sito ufficiale](https://git-scm.com/)
[Documentazione](https://git-scm.com/book/en/v2)
[Getting Started](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
[Git Basics](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
[Git Branching](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)


- **Tools & Lab**

### Advanced
- **Obiettivi**
	- Saper effettuare un rebase di un branch rispetto al repository master e risolvere interattivamente eventuali conflitti;
	- Saper usare le funzionalità di stashing;
	- Saper modificare la history di un repository;
	- Saper utilizzare i comandi cherry-pick, diff e log;
  
- **Link Utili**
[Sito ufficiale](https://git-scm.com/)
[Documentazione](https://git-scm.com/book/en/v2)
[Branching and Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
[Interactive Staging](https://git-scm.com/book/en/v2/Git-Tools-Interactive-Staging)
[Stashing and Cleaning](https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning)
[Rewriting History](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
[Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
[Cherry Pick](https://git-scm.com/docs/git-cherry-pick)
[Diff](https://git-scm.com/docs/git-diff)
[Log](https://git-scm.com/docs/git-log)
  
## SVN
### Basic
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

### Advanced
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

# EAI (Enterprise Application Integration)
- **Obiettivi**
1. General concepts pertaining system integration
2. Integration Styles
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. File Transfer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Shared Database
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Remote Procedure Invocation
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Messaging 
3. Messaging Systems
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Message Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Pipes and Filters
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Message Router
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Message Translator
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Message Endpoint
4. Messaging Channels
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Point-to-Point Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Publish-Subscribe Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Datatype Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Invalid Message Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Dead Letter Channel
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Guaranteed Delivery
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Channel Adapter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Messaging Bridge
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Message Bus
5. Message Construction
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Command Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Document Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Event Message
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Request-Reply
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Return Address
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Correlation Identifier
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Message Sequence
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Message Expiration
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Format Indicator
6. Message Routing
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Content-Based Router
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Message Filter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Dynamic Router
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Recipient List
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Splitter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Aggregator
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Resequencer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Composed Msg. Processor
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Scatter-Gather
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> j. Routing Slip
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> k. Process Manager
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> l. Message Broker
7. Message Transformation
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Envelope Wrapper
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Content Enricher
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Content Filter
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Claim Check
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Normalizer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Canonical Data Model
8. Message Endpoints
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Messaging Gateway
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Messaging Mapper
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Transactional Client
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Polling Consumer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Event-Driven Consumer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Competing Consumers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b  Message Dispatcher
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Selective Consumer
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Durable Subscriber
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Idempotent Receiver
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Service Activator
- **Link Utili**
[Integration theory guide](http://www.enterpriseintegrationpatterns.com/Introduction.html)

## JMS
- **Obiettivi**
1. What is a Messaging system?
2. JMS API and related Concepts
3. JMS API Programming Model
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Connection Factories
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Destinations
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Connections
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Sessions
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Message Producers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. Message Consumers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. Message Listeners
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. Message Selectors
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. Messages
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> j. Message Headers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> k. Message Properties
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> l. Message Bodies
- **Link Utili**
[JMS Guide (relevat topics up to chapter 3 included)](http://docs.oracle.com/javaee/1.3/jms/tutorial/1_3_1-fcs/doc/jms_tutorialTOC.html)
- **Tools & Lab**
Lab: Installation of a EMS server on the previously created Centos 6.5 VM.
Lab: Creation of a centos VM using vagrant. [Link to vagrant guide](https://docs.google.com/document/d/1kypDQ33wxUAE1-_Cm94UNwGtmWy0_UGw5SePVHutzws/edit?usp=sharing )
Lab [KP linux exercises](https://drive.google.com/open?id=0BydghG4Au4HfUzFobUxTU0wtV1E)

## SOA
- **Obiettivi**
1. Service Oriented Architecture paradigm concept 
2. Service design principles
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Standardized service contract
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Service loose coupling
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. service abstraction
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. service reusability
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. service autonomy
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. service statelessness
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> g. service discoverability
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> h. service composability
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> i. interoperability
3. Service orientation and the concept of applicazione soa
4. Service orientation e il concept of integrazione inside soa
5. Service models
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. service layers
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. entity services
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. task services
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. utility services
6. Undertanding the difference between the  top down and the bottom up delivery strategies
- **Link Utili**
[SOA theory guide](http://serviceorientation.com/serviceorientation/index)
[SOA review blogspot](http://savedev.blogspot.it/2013/09/spaghetti-integration-to-soa.html)
[SOA tutorial](http://soaschools.com/)

# Algoritmi e strutture dati
### Basic
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

### Advanced
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

# Logs
### Basic
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

### Advanced
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

# Software Lifecycle
### Basic
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

### Advanced
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

# Web e Application Servers
### Basic
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

### Advanced
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

# Web Services (SOAP/REST)
### Basic
- **Obiettivi**
1. Difference between API and Web Services
2. Inner workings of web services
3. Why use web services?
- **Link Utili**
[Difference between API and web services explained 0](https://www.linkedin.com/pulse/difference-between-api-web-service-chitrakannan-balasubramanian/)
[Difference between API and web services explained 1](https://testautomationresources.com/api-testing/differences-web-services-api/)

### SOAP, WSDL
- **Obiettivi**
1. wsdl elements (types, message, operation, portType, binding)
2. Definition of data types using xml schema
3. Definition of messagges
4. Definition of operations
5. Definition of portType
6. Definition of binding
7. abstract wsdl vs concrete wsdl
8. The usage of SOAP as an applicative protocol 
9. SOAP syntax
10. SOAP Envelope
11. SOAP Header
12. SOAP Body
13. SOAP Fault
- **Link Utili**
[w3 school xml_services](https://www.w3schools.com/xml/xml_services.asp)
[guide to web services](http://www.html.it/guide/guida-web-service/)
- **Tools & Lab**
[Tool: Download SoapUi](https://www.soapui.org/downloads/soapui.html)
[Tool: Soap UI Mock]( https://www.soapui.org/soap-mocking/working-with-mockservices.htm)

### RESTful
- **Obiettivi**
1. Web service definition
2. Elements of a wsdl (types, message, operation, portType, binding)
3. Definition of data types using xml schema
4. Definition of messagges
5. Definition of operations
6. Definition of portType
7. Definition of binding
8. abstract wsdl vs concrete wsdl
9. The usage of SOAP as an applicative protocol 
10. SOAP syntax
11. SOAP Envelope
12. SOAP Header
13. SOAP Body
14. SOAP Fault
- **Link Utili**
[w3 school xml_services](https://www.w3schools.com/xml/xml_services.asp)
[guide to restful web services](https://www.html.it/guide/restful-web-services-la-guida/)
[rest vs soap](https://www.html.it/pag/19612/differenze-tra-web-service-rest-e-soap/)
- **Tools & Lab**
[Tool: Download Postman](https://www.getpostman.com/downloads/)
[Tool: Download Swagger]( https://swagger.io/tools/swagger-editor/download/)

# Design e Architectural Patterns
### Basic
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab

### Advanced
- **Obiettivi**
Obiettivo1
Obiettivo2
Obiettivo3
- **Link Utili**
[Link1](http://)
[Link2](http://)
- **Tools & Lab**
[Tool1](http://)
Lab



