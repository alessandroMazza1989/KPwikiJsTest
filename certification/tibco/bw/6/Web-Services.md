---
title: Web-Service
description: 
published: true
date: 2021-06-07T13:07:06.114Z
tags: 
editor: markdown
dateCreated: 2021-06-07T12:59:19.651Z
---

# Web Services

## Un cliente chiede di poter chiamare un web service in un processo: quale soluzione gli consigli?
Risposta: Invoke palette
## Comando OSGI che permette di vedere gli endpoints REST e SOAP contemporaneamente
Risposta: lendpoints
## Which OSGi command returns an overview of both the REST and SOAP HTTP endpoints?

showendpoints
lrestdoc
listendpoints
**lendpoints**

## With which two sources can TIBCO Designer create web services? (Choose two.)

**Process Defnition**
HTTP Receiver
JMS Queue Subscriber
**WSDL**
SOAP Retrieve Resource

# REST

## What is Representational State Transfer (ReST)?

a. An industry specification
b. **An architectural style**
c. An architectural specification
d. An Architectural standard
e. An industry standard
## Da un form web si vuole convertire l'informazione per invocare un servizio rest. La domanda era più o meno quale standard utilizzare?
Risposta: Tra le risposte c'era utilizzare JSON 
## Che cosa utilizza il servizio Rest per gestire le informazioni?
Risposta: JSON
## Come configurare il service resource path di un servizio rest per abilitarlo alla modalità partial response rest
Risposta: il resource path deve contenere la keyword "fields" come query parameter.
Posso metterlo anche con "Add query parameters" nel binding. 
Esempio:/banca/fields{nome,cognome,idconto
## You need to create a RESTful service in TIBCO ActiveMatrix BusinessWorks for an employee resource that has the following fields: ID, FirstName, LastName, Salary. How should you configure the Resource Service Path for a service that returns the employee resource by ID?
Risposta: /employee/{id}
## You need to create a RESTful service in TIBCO ActiveMatrix BusinessWorks for an employee resource that has the following fields: ID, FirstName, LastName, Salary. How should you configure the Resource Service Path for a service that returns the employee resource by ID?
 
/employee/[id]
**/employee/{id}**
/employee/(id)
/employee/id

## Domanda inerente il PARTIAL REST (da studiare). Fare attenzione perché le risposte vengono presentate senza chiusura di }
es. /employee/{Fields
## You need to create a single REST service that has a Get Operation for an Employee resource. The resource has various fields, including FirstName, LastName, Age. Which resource service path should you provide to develop a single RESTful service that can use the partial response feature provided by Tibco ActiveMatrix BusinessWorks?
/employees?{field
/employees/{field?{ResponseType
/employees/{field
**/employees/field?{FirstName&{LastName&{Age**
## Rest studiare rest partial

## Securing un servizio REST con Basic Authentication.
Check Authentication sull’HTTP Connector + Identity Provider + Check Authenticate sul binding della risorsa.
Nota: questa procedura non è più utilizzabile di default sulle versioni recenti
## Come mandi un attachmenti a un servizio REST.
Risposta: Request type settato a Custom e setto Content-Type con il tipo di attachment.
## Come faccio una chiamata rest con attachment
Da studiare -- MIME Part in HTTPSendRequest?
## Configurare tutte le applicazioni in modo che possano usare il REST SERVER con un’unica documentation URL. Dove va impostato?
Risposta: Appspace

## Domanda inerente al securing bwagemt REST API

## You deploy a REST application to an AppSpace with two AppNodes on the same machine. Where should you set the swagger doc properties so that every AppNode can host the swagger docs independent…
           	
**AppNode**
AppSpace
Domain
Bwagent
## You deploy a Rest application to an AppSpace with two AppNodes on the same machine. Where should you set the swagger doc properties so that every AppNode can host the swagger docs independently?
**AppNode**
Domain
bwagent
AppSpace

## While testing a RESTful service in Tibco BusinessStudio, the parameter com.tibco.bw.binding…response to be sent in the console.
In which file should you set this parameters?
           	
config.xml
**config.ini**
logback.ini
logback.xml

## You need to create a RESTful service with support for Basic Authentication. Which two steps are necessary in order to implement the solution? (Choose 2 answers)

Check the Authentication checkbox on the Identity Shared Resource
Check the Authenticated checkbox on the REST Service Binding Configuration
**Check the Authentication checkbox on the HTTP Client Shared Resource**
Check the Authentication checkbox on the HTTP Connector Shared Resource
**Check the Authentication checkbox on the HTTP Proxy Shared Resource**

## A company wants to implement basic authentication in their BusinessWorks 6 REST service. What does a developer have to do to achieve this goal?

**Enable authentication on the HTTP Connector Resource, specify an Identity Provider, and enable Authentication in the Component Configurations**
Enable authentication on the HTTP Connector Resource, specify an SSL Server Configuration, and enable Authentication in the Component Configurations
Enable Confidentiality on the HTTP Connector Resource, specify an SSL Server Configuration, and enable Authentication in the Component Configurations
Enable authentication on the HTTP Connector Resource, specify an LDAP shared resource, and enable Authentication in the Component Configurations
## Come è possibile passare in input ad un RESTful service un contenuto binario?

XML
**JSON**
BINARY
CUSTOM

## What is the correct way to add parameters to a ReST operation?
a. %%parameter%%
b. [parameter]
c. (parameter)
d. **{parameter}**


## What are two functions of Invoke REST API activity? (Choose two)
a. **Invokes RESTful web services**
b. **Sends synchronous request and receives response from service provider**
c. Provides RESTful web services
d. Sends asynchronous request and receives response from service provider
