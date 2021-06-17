---
title: Lista-Domande
description: 
published: true
date: 2021-06-17T13:32:59.563Z
tags: 
editor: markdown
dateCreated: 2021-06-17T13:13:09.808Z
---

# Lista-Domande

## What are the three options available to define the engine persistence mode at an AppSpace level? (Choose three.) 

**memory**
cache
**datastore**
file
**group**
exclusive

## When configuring bwagents, which two options are available for setting the persistence and the transport provider? (Choose two.)
 
**ActiveSpaces**
EMS
**DBEMS**
TCP
NFS

## Your company requests that you set up managed fault tolerance for applications deployed on AppSpace A1. How should you configure the engine persistence modes and requirements in order to fulfill the request?
 
A.Engine persistence mode must be set to memory, and TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them.
B.Engine persistence mode must be set to datastore, and TIBCO ActiveSpaces must be configured to let AppNodes communicate between them.
**C.Engine persistence mode must be set to group, TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them, and a database is required for persistence.**
D.Engine persistence mode must be set to TIBCO ActiveSpaces, TIBCO Enterprise Message Service must be configured to let AppNodes communicate between them, and a database is required for persistence.

## What does degraded state indicate for an AppSpace? 
 
The config file for the AppSpace has incorrect values.
**The AppSpace does not have the minimum specified AppNodes.**
The AppSpace is opened in an earlier version of TIBCO ActiveMatrix BusinessWorks.
The domain was moved from local to enterprise mode.

## You need to define a process that can only be invoked by other processes that are a part of the same package. Which modifier should the process have? 
 
public
static
**private**
protected

## You need to create a RESTful service in TIBCO ActiveMatrix BusinessWorks for an employee resource that has the following fields: ID, FirstName, LastName, Salary. How should you configure the Resource Service Path for a service that returns the employee resource by ID?
 
/employee/[id]
**/employee/{id}**
/employee/(id)
/employee/id

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

## A large data set needs to be passed from a parent to multiple inline child processes. The variable has to be visible to processes across different modules. Which variable is correct to use in this situation?
 
substitution variables
module shared variables
application shared variable
**job shared variables**
 
## Where can a fault handler be attached in a process? (Choose two.)
 
Service Binding Level
**Process Level**
**Scope Level**
Reference Binding Level
Application Module Level
 
## Which activity allows you to collect multiple transition flows to resume a single flow of execution in the process?
 
**Empty activity**
Null activity
Exit activity
Scope activity

## You are using a Mapper activity in your process design. Which three can be used as inputs in the Mapper Input tab? (Choose three.)
 
**Primitive Datatype**
Database Resultset
DTD File
**Inline Schema**
**Complex Datatype**
CLOB
 
## You are migrating an application, which includes some custom XPath functions. Which runtime task is needed to make the custom function available?
 
Include the custom XPath function plug-ins into the Host repository.
Export the XPath function as a zip, and import it through BusinessStudio.
Export the XPath function as a jar, and update the bwagent path.
**Include the XPath function plug-ins in your application.**

## While debugging an application inside TIBCO BusinessStudio, when is the job data visible in the job data view?
 
**after selecting an activity in a job**
after selecting an activity in completed jobs only
a Process Definition that implements the operations of the service
after selecting a completed job
after selecting the job data view

## You deploy a REST application to an AppSpace with two AppNodes on the same machine. Where should you set the swagger doc properties so that every AppNode can host the swagger docs independent… 
	
**AppNode**
AppSpace
Domain
Bwagent

## You are using machines in multiple environments. They have Tibco Active Matrix Business Works installed and are in the same IP subnet. You need to ensure that the machines from one environment are not able to connect to another environment. You must achieve this goal without using additional network technology. 

Ensure that all agents that belong to an environment have the same agent name
Ensure that all machines that belong to an environment have the same machine name
**Ensure that all agents that belong to an environment have the same network name**
Ensure that all machines that belong to an environment have the same network name

> Tutti gli agent dello stesso ambiente devono avere la stessa bw agent network. Crei due bw agent network, uno per ogni ambiente.
{.is-info}

## Which Statement is true when setting up a multi-agent, multi-machine environment using Tibco Active Matrix technology type for a simple server configuration ?
**There as to be at least one server in the bwagent network**
There as to be at least one server and a remote client
There as to be at least two clients in the bwagent network
There as to be at least two server in the bwagent network


## Which to database driver require additional configuration in other to be used with Tibco Active Matrix BW? (Choose two.)
HSQLDB driver
**MySQL Database driver**
**Oracle Database driver**
Microsoft SQL Server driver
Postgress SQL driver

## While testing a RESTful service in Tibco BusinessStudio, the parameter com.tibco.bw.binding… response to be sent in the console. In which file should you set this parameters?
config.xml
**config.ini**
logback.ini
logback.xml

## You Have to create a SOAP Service that receives a JPEG image as an attachment. How must you create the WSDL for this service in other to achieve this goal?
A part of the input of the WSDL message must be of type xs:BLOB and configured as an attachment.
In a concrete WSDL, the attachment is described as a mime part of the multipart message.
**A part of the input of the WSDL message must be of type base64binary and configured as an attachment. In a concrete WSDL, the attachment is described as a mime part of the multipart message**
A part of the input of the WSDL message must be of type BLOB. In a concrete WSDL, the attachment is describes as a mime part of the singlepart message
A part of the input of the WSDL message must be of type base64binary and configured a part of message. In a concrete WSDL, the attachment is describes as a mime part of the singlepart message

## You are required to create a SOAP HTTP Service. In the service implementation, you also need the transport context. Which steps are required to be performed in the process?
Create a schema for the HTTP Transport Context, and use the Set Context activity in the process
Create a Context Resource for the HTTP Transport context, and use the Get Context activity in the process
Create a Context Resource for the HTTP Transport context, and use the Set Context activity in the process
**Create a schema for the HTTP Transport Context, and use the Get Context activity in the process**


## Which two actions must be performed for an Oracle driver to be used inside BusinessWorks environment? (Choose two.)

**Use the bwinstall utility**
Copy the JDBC jar file to any folder in the RunTime Classpath
**Copy the JDBC jar file to the Tibco third-party JDBC Driver folder**
Use the bwadmin utility
Copy the JDBC jar file in the bwagent lib folder

## As a network administrator, you want to create an agent network so that bwagents can communicate with across multiple computers. What are the two technology types that allow to achieve this goal? (Choose two.)
Database with Tibco Rendezvous
Apache Cassandra with TIBCO Enterprise Message Service 
Database with TIBCO FTL
**TIBCO ActiveSpaces**
**Database with TIBCO Enterprise Message Service**



## What is the appropriate command line option to use when uploading Tibco BusinessWorks Application to a non- …archive location named QA 
bwadmin  upload archive/QA application.ear –d MyDomain
bwadmin  upload –d MyDomain archive/QA application.ear
bwadmin  upload –path archives/QA application.ear –d MyDomain
**bwadmin  upload –d MyDomain –path /QA application.ear **
	
## Which runtime entity is required to run in an enterprise mode using the default domain data storage? 
DataBase Server
**bwagent**
bwdesign
Tibco Enterprise Message Service
Seconda Domanda. Quale entità runtime viene utilizzata per creare runtime entity in ambiente enterprise?
Risposta: bwadmin

## Which two Adapter Palette activities are Process Starters? (Choose two.)
Receive Adapter Request 
**Adapter Request-Response Server**
**Adapter Subscriber**
Send Adapter Response
Wait for Adapter Request

## A custom XPath function associated with mapper activities in Active Matrix BusinessWorks processes ..deprecated. How can the custom XPath function be removed from the mapper?

Uninstall the custom XPath function from the application module
Uninstall the custom XPath function plug-in from the application project
**Uninstall a custom XPath function by using Help > About Tibco ActiveMatrix BusinessWorks Menu**
Uninstall a custom XPath function by using File > Tibco ActiveMatrix BusinessWorks Menu

## You are defining a process that uses the JMS Send Message activity to send a message to a backend application. this application replies asynchronously and does not maintain the other of messages. Which activity should you use if you need to correlate the replies from this application back in your original process?
Wait for JMS Request
JMS receive message
Get JMS queue message
**JMS Request Reply**

## Which type of activity is require to implement an asynchronous event in a running process and the ….executing the process instance when an appropriate event is received?
Event handler activity
Process Starter activity
Regular activity
**Signal-in activity**

## During development, one of your peers asks you for help on how to call an external ….. Which activity should you recommend that they use?
Invoke API activity
**Invoke activity**
HTTP Request/Response activity
SOAP Request/Reply activity

## 	Which statement is true when setting up a multi-machine environment us……technology type for a simple server configuration?
**There has to be at least one server in the bwagent network**
There has to be at least one server and the remote client
There has to be at least two clients in the bwagent network
There has to be at least two servers in the bwagent network

## …a SOAP service by using JMS as transport. One part of the message is an attachment. The architect of your ….requests for you to forward the message to a JMS Queue; however, you may only forward a reference to the…. And not the attachment itself.
… process implementation, write the attachment to file, and use the output of the Write File acrivity to obtain a reference to the file containing the attachment
… process implementation, write the attachment to file, and use the Get Context activity to obtain a reference to the file containing the attachment
**…SOAP Service Binding, set the persistence file, and use the Get Context activity to obtain a reference to the file containing the attachment**
…SOAP Service Binding, set the persistence file, and use Read File activity to obtain a reference to the file containing the attachment

## As a network administrator, you are told to create an agent network and provide access via REST for managing the TIBCO AM BW applications, AppNodes, and AppSpaces. This URL should be accesible from other machines. How will you configure the bwagent?

Start the bwagent with the apiserver option, and configure the hostname in bwagent.xml
**Start the bwagent with the apiserver option, and configure the hostname in bwagent.ini**
Start the bwagent with the apiserver option, and configure the hostname in bwagent.tra
Start the bwagent with the apiserver option, and configure the hostname in config.ini

## You have a TIBCO ActiveMatrix BW application running on multiple AppNodes, which are part of the same AppSpace. You want to read or update the module shared variable state. Which option should you select?

bw.engine.persistenceMode = “AppSpace”
**bw.engine.persistenceMode = “group”**
bw.engine.persistenceMode = “datastore”
bw.engine.persistenceMode = “true”

## How do you create runtime entities with the deployment mode set to local?
Create the runtime entities while installing the product.
Local mode uses default runtime entities created by the bwagent.
Use TIBCO Enterprise Administrator to create runtime entities.
**Use BwAdmin to create runtime entities.**

## You have configured your bwagent to run in enterprise mode. What are the two different utilities that you can use to deploy your application? (chose two)
TIBCO Administrator
bwdesign
bwinstall
**TIBCO Enterprise Administrator**
**bwadmin**

## How do you generate the config file for an AppSpace?
**Run the command: bwadmin config -d myDomain -a myAppspace -cf <temporaryLocation>/config.ini**
Run the command: bwinstall config -d myDomain -a myAppspace -cf <temporaryLocation>/config.ini
Run the command: bwdesign config -d myDomain -a myAppspace -cf <temporaryLocation>/config.ini
Copy the config file from the samples directory


## You need to perform a Remote Deployment from BuisnessStudio by using the Deployment Servers view. Which utility do you need to have running in order to archive this? 

bwadmin
bwinstall
**bwagent**
bwdesgin

## You have two machines configured in an agent network. A domain and AppSpace span across both machines. Each machine had a single AppNode, which is part of the same AppSpace. Which utility allows you to deploy an application to the AppSpace so that it runs on each AppNode? 

bwinstall
bwdesign
bwdesign
**bwadmin**


## A Tibco AM BW application will be deployed on both Windows And Linux Servers; the application uses a property named Path that uses the appropriate operating system syntax to point the files in the file system. How can you specify different configuration of the variables that the application uses?

by using a variable insted of a Property
**by creating different Application Profiles**
by defining the path property ad a Process Property
by creating different Application Module Profiles
