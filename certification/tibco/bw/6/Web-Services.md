---
title: Web-Service
description: 
published: true
date: 2021-06-08T15:44:57.758Z
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
Risposta: **/employee/{id}**
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

# SOAP
## Come esporre lo stesso servizio soap contemporaneamente "soap over jms" e "e over http"
Risposta: doppio binding sulla stessa operation
## Come gestire il retry di chiamata soap quando il servizio non è attivo (tre volte)
Risposta: Repeat on error
## Mandare un attachment bitmap in un servizio soap. (ce n’era una simile)

## Inviare attachment su servizi SOAP
Risposta: Service Binding Request Context + palette SetContext
## You are developing a process that needs to invoke a SOAP service. During development, the endpoint that hosts the service is located at http://development.example.org. During production, the endpoint that hosts the service is located at http://production.example.org. How do you ensure that the endpoint you are accessing is configurable?
Risposta: Associate an HTTP Client with the transport configuration in the component bindings, and set the endpoint in the HTTP Client.
## You are developing a process that needs to invoke a SOAP service. During development, the endpoint that hosts the service is located at http://development.example.org. During production, the endpoint that hosts the service is located at http://production.example.org. How do you ensure that the endpoint you are accessing is configurable?
 
Use the SetEPR activity in the process and have a module property that references the endpoint.
**Associate an HTTP Client with the transport configuration in the component bindings, and set the endpoint in the HTTP Client.**
Set the endpoint in the advanced section of the Invoke activity, and use a module property that references the endpoint.
Create a module property called soapServiceEndpoint., and use that to set the correct endpoint.

## Which three Shared Resources does this process use? (Choose three.)
 
**JDBC Connection**
ODBC Connection
**JMS Connection**
**HTTP Connector**
HTTP Client
RESTFul Connector

## Come impostare la Basic Authentication su SOAP?

## You Have to create a SOAP Service that receives a JPEG image as an attachment.
How must you create the WSDL for this service in other to achieve this goal?

-A part of the input of the WSDL message must be of type xs:BLOB and configured as an attachment. In a concrete WSDL, the attachment is described as a mime part of the multipart message.
**-A part of the input of the WSDL message must be of type base64binary and configured as an attachment. In a concrete WSDL, the attachment is described as a mime part of the multipart message**
-A part of the input of the WSDL message must be of type BLOB. In a concrete WSDL, the attachment is describes as a mime part of the singlepart message
-A part of the input of the WSDL message must be of type base64binary and configured a part of message. In a concrete WSDL, the attachment is describes as a mime part of the singlepart message

## You are required to create a SOAP HTTP Service. In the service implementation, you also need the transport context. Which steps are required to be performed in the process?

-Create a schema for the HTTP Transport Context, and use the Set Context activity in the process
-Create a Context Resource for the HTTP Transport context, and use the Get Context activity in the process
-Create a Context Resource for the HTTP Transport context, and use the Set Context activity in the process
**-Create a schema for the HTTP Transport Context, and use the Get Context activity in the process**

## Soap con attachment ma il cliente non vuole che venga inviato l’allegato, bensì solo il contenuto dello stesso. (Studiare)

## ... a SOAP service by using JMS as transport. One part of the message is an attachment. The architect of your ….requests for you to forward the message to a JMS Queue; however, you may only forward a reference to the…. And not the attachment itself.

-…process implementation, write the attachment to file, and use the output of the Write File acrivity to obtain a reference to the file containing the attachment
-… process implementation, write the attachment to file, and use the Get Context activity to obtain a reference to the file containing the attachment
**-…SOAP Service Binding, set the persistence file, and use the Get Context activity to obtain a reference to the file containing the attachment**
-…SOAP Service Binding, set the persistence file, and use Read File activity to obtain a reference to the file containing the attachment

## You create a SOAP service by using JMS as transport. One part of message is an attachment. The architect of your company requests for you to forward the message to a JMS Queue; however, you may only forward a reference to the attachment and not the attachment itself. What are the required steps to meet this request?

**In the SOAP Service Binding, set the persistence to file, and use the Get Context activity to obtain a reference to the file containing the attachment**
In the process implementation, write the attachment to file, and use the Get Context activity to obtain a reference to the file containing the attachment
In the SOAP Service Binding, set the persistence to file, and use the Read File activity to obtain a reference  to the file containing the attachment
In the process implementation, write the attachment to file, and use the output of the Write File activity  to obtain a reference  to the file containing the attachment

