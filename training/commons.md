---
title: Common Topics
description: Indice degli argomenti comuni
published: true
date: 2020-04-20T16:07:05.761Z
tags: commons, software versioning, git, networking, pattern, design, web services, unix, shell, wsdl, soap, rest, server, algoritmi, databases, sql, relational, lifecycle, log
---

In questa sezione verranno trattati i principali argomenti che rappresentano la base di una formazione specialistica.
Individuare le sezioni di interesse insieme al proprio tutor.
<p>&nbsp;</p>

# Networking
Intro
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
# Unix Shell
Intro
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


# XML/XSD/XPATH/XSLT
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

# Databases
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



