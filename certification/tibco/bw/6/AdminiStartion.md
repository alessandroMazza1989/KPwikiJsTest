---
title: Administration
description: 
published: true
date: 2021-06-07T10:52:01.034Z
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
