---
title: Lista-Domande
description: 
published: true
date: 2021-06-17T16:04:25.037Z
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

## You need to activate your process on a different AppNode, but only if the existing AppNode fails. Which Activation setting should you use to achive this goal?

Fallover AppNodes
Multiple AppNodes
Elastic AppNodes
**Single AppNode**

## What does an out-of-sync status mean after deployng an application to an AppSpace? (Choose Two) 

A bwagent configuration failed to start.
**A bwagent is not reachable due to network failure.**
**A bwagent configuration may not have been applied remotely.**
A bwagent is not reachable because the AppNode is stopped.
A bwagent is stopped.


## Which two TIBCO AM BW project resource can be configured in TIBCO BuisnessStudio? (choose two) 

**TIBCO BusinessConnect Applications**
**OSGI-based Java Applications**
C Applications
C++ Applications
Process-Driven Application


## While configuring a JDBC Query activity, the JDBC Connection does not show up in the resource list. What is the issue?

The JDBC Connection was configured in JAVA Module.
The JDBC Connection was configured in the current Application Module.
The JDBC Connection was configured in a different Shared Application Module.
**The JDBC Connection was configured in a different Application Module.**

## You are given a WSDL has two distinct operations in a single Port Type. You need to implement this WSDL by using TIBCO AM BW. What should you do?

Create a single process, and use a recive activity for both operations.
Create two applications that implement both operations, and set the activation mode to single.
**Create a single process, and use a constructor for both operarions.**
Create two processes, and remove one operation in both processes.



## You need to synchronize multiple Critical Section groups that can be part of different process instances.
What should you do to accomplish this goal?

Increase the Timeout of the Critical Section to allow for all the different process instance to synchronize.
**Create a Shared Lock in your Critical Section with a Module Shared Variable as Shared Variable Type.**
Change the Group Type from Critical Section to Local Transaction.
Create a Shared Lock in your Critical Section with a Job Shared Variable as Shared Variable Type.


## You have a situation in which an external source supplies an XSLT file to perform the trasformation, and you want to leverage the file. Which activity helps you accomplish this goal?

Mapper
**Transform XML**
Invoke XSLT
Render XML


## In which of the following cases shoud you use Coercion in a Mapper Activity?

**When the input data type is unknown, and the output data type is know.**
When the input data is repeating, and the output data is not.
When the input data is not repeating, and the output data is repeating.
When the input data type is known, and the output data type is unknown.


## Which configuration is required to implement a switch case in a mapper activity within a process flow?

Repeatitive Group
Surround With Scope
**Surround with Choice**
Non-Repeatitive Group


## You need to design a TIBCO AM BW Process so that you maintain the context from previous processes istance.Which feature should you use?

dialogues
shared variables
**conversations**
context variables



## In which scope would you place a Rethrow activity?
  
**Fault Handler**
Compensation Handler
Transaction Scope
Event Handler


## A TIBCO AM BW application has to post a transaction by calling an external Web Service. The business Requirment is to attempt the call to web service at least three times if the service is not available. Which group type can be used for this scenario?

ForEach
Iterate
Repeat
**RepeatOnError**


## What should you configure in order to define Startup Process tasks for a given application?

Startup Process
Main Process
Initiator Process
**Activator Process**


## Select the appropriate shared resource to associate with the task: 

Transfers email messages between servers SMTP Resource **[STMP Resource]**
Contains the specification for parsing or rendering a text string **[Data Format]**
Represents an outgoing HTTP connection with a SOAP binding  **[HTTP Client]**
Provides a way to configure the JNDI provider for a JMS Connection **[JNDI Configuration]**

## You need to define an Event Handler for asynchronous processing for a given process.
At which levels can you create an event handler?

Scope Level and Activity Level
**Scope Level and Process Level**
Module Level and Process Level
Activity Level and Process Level


## You have a scope variable within a scope, and you want to override a process variable. Which activity allows you to override the process variable?

Mapper Activity
**Set Shared Variable Activity** *(Possibile Risposta se Scope Variable)*
**Assign Activity** *(Possibile Risposta se Process Variable)*
Get Shared Variable Activity


## You need to cancel an online order and ensure the money is returned to the customer. Which method in TIBCO AM BW allows you to most effectively manage, execute, or revert a Unit Of Work so that you can achieve this goal?

Define an error handler in a scope.
**Define a conversation.**
Define an error transition.
Define a repeat on error activity


## A Custom xPath function has been created in a TIBCO AM BW Project. How can the function be made available (at design time) to other project? (Choose two)

**by installing it into host repository deployable plug-ins and fragments.**
**by exporting the deployable plug-ins and fragments.**
by exporting the custom xpath function resource
by installing the Custom xpath function into TIBCO AM BW target project
by adding the custom Xpath function to a target project



## Which three TIBCO AM BW artifacts can be designed using TIBCO Business Studio? (Choose Three)
bwagent network 
**applications**
AppNode
**application module**
**shared module**
domain


## If there are five agents in an agent network, and they have to be managed through a TIBCO Enterprise Administrator Server, how many of them must be registered?
2
**1**
5 
3


## TIBCO ActiveMatrix BusinessWorks agents on machines M1, M2, and M3 are configurated with TIBCO ActiveSpaces as the persistence and transport technology. M1 and M2 are configured ad servers. Assume all agentes are started on port 5060. For M3 to act as a remote client, which property should you set on all agents so that M3 would remain unaffected if mahine M1 goes down? 

remoteListenURL on M1 and M3; remoteDiscoveryURL on M2
remoteDiscoveryURL on M1 and M3; remoteListenURL on M2
remoteDiscoveryURL on M1 and M2; remoteListenURL on M3
**remoteListenURL on M1 and M2; remoteDiscoveryURL on M3**
  
* in aggiunta M3 role=remoteclient remoteDiscoveryURL=tcp://Machine1:5060;Machine2:5060 (remoteListenURL M1;M2) ….M3 discoveryUrl*

## Which two shared module functionalities are exported to the application and other shared modules? (Choose two)

**Shared Resources**
Private processes
Service Bindings
**public processes**
reference bindings


## TIBCO Enterprise Administrator cannot find a domain. Whats is the problem? Da rivedere, Nicola porta in local mode

**The domain was created in local mode.**
The domain was created in enterprise mode.
The TIBCO Enterprise Administrator cannot access the local file system.
The TIBCO Enterprise Administrator cannot connect to the database.


## Which three statements are true about bwadmin backup and restore commands in an enterprise mode? (choose three)

**The backup command exports the current state of the environment to a command file.**
The bwadmin backup command and the bwadmin restore command are complementary.
**The restore command restores the file system of a bwagent to the state of the persistent datastore.**
**The bwadmin backup command and the bwadmin restore commad are not complementary.**
The backup command exports the current state of the environment to a datastore.
The restore command restores the file system of a bwagent to the least checkpoint state of a datastore.

## You deploy a Rest application to an AppSpace with two AppNodes on the same machine.
Where should you set the swagger doc properties so that every AppNode can host the swagger docs independently?

**AppNode**
Domain
bwagent
AppSpace

## What is the default setting for the log level of an AppNode log file?
  
**ERROR**
INFO
WARN
DEBUG


## The TIBCO AM BW architect requests the application developer to desgin applications that allow high availability. Which three configuration properties should be set so that managed fault tollerance is implemented? (Choose three)
  
bw.engine.persistenceMode=datastore
a minimum of two AppNodes across two AppSpaces
**Process Activation In Business Studio**
**bw.engine.persistenceMode=group**
Process Mode in Business Studio
**a minimum of two AppNodes in an AppSpace**


## At a minimum, which two properties of a bwagent must be configured for a multi-agent., multi-machine environment that uses TIBCO ActiveSpaces for persistence and transport? (Choose three)

bw.agent.technology.as.remoteDiscoveryURL
bw.agent.technology.as.clientURL
**bw.agent.technology.as.discoveryURL**
**bw.agent.technology.as.listenURL**
bw.agent.technology.as.server
**bw.agent.technology.as.role**
    

## An application you have created with activation set to Single AppNode is deployed into an AppSpace consisting of two AppNodes (A1 and A2). One of the administrators accidentally stops AppNode A1. What is the expected behavior of your application?

The application will be activated on A2, but no requests are processed.
The application is standby on A2, and no requests are processed.
The application will be activated on A2, and requests are processed.
**The application is stopped on A2, and no requests are processed.**

## Which two statements are true about the fault tolerance feature of TIBCO AM BW applications?
(Choose two) 

Managed fault tolerance requires persistence mode to be set memory, while non-managed fault tolerance requires persistence mode to be set to group.
Managed fault tolerance requires activation mode to be set to Single AppNode, while non-managed fault tolerance requires activation mode to be set to Multiple AppNode.
**In Managed fault tolerance, AppNode are aware of other AppNodes in the AppSpace, while in non-managed fault tolerance, AppNodes are unaware of other AppNodes in the AppSpace.**
**Managed fault tolerance requires persitance mode to be set to group, while non-managed fault tolerance requires persistence mode to be set to datastore.**
Managed fault tolerance supports checkpointing, while non-managed fault tolerance does not support checkpointing.


## Which statement is true when setting up a multi-agent, multi-machine enviroment using TIBCO AS as the technology type for a simple server configuration?

There has to be at leats two clients in the bwagent network.
There has to be at least one server and a remote client.
**There has to be at least one server in the bwagent network.**
There has to be at least two servers in the bwagent network.
  
## The Tibco Enterprise Administrator as multiple components, such as the server, the agent, and the server UI. Which communication mechanism do the server and the agent component use to talk to each other?
  
Shared file system
Tibco Enterprise Message Service
Tibco Rendezvous
**Rest API**


## A Tibco ActiveMatrix BusinessWorks application connects to a database and the Tibco EMS instance. On deployment, a system administrator has to replace the connection parameters to the production database and EMS instance. Which type of properties can be used from the Tibco Enterprise Administrator solution to modify this connection’s parameters? 
  
Module Properties
**Application Properties**
Process Properties
Global Variable
 
## What is indicated if the engine persistence mode (bw.engine.persistenceMode) is set to type group? 
  
**ActiveMatrix BusinessWorks Environment is in managed fault tolerance mode**
The engines are unaware of the existence of each other
Each AppNode in a AppSpace has a unique database specified at the AppNode level
ActiveMatrix BusinessWorks Environment is in non-managed fault tolerance mode
 
## Which to statements are true about a bw.engine.persistenceMode that is set to group? (Choose 2 answers)
  
The non-managed fault tolerance feature requires this properties
The database connection configuration must be specified only at the AppNode level
The engine does not require a database to be configured
**The engine required a group provider such as Tibco Enterprise Message Service to be configured**
**The group mode supports the Checkpoint activity and other persistence features**
 
## If you need the loop through every User record in a database, which scope should you use?
  
**Iterate**
PichFirst
If
RepeatOnError
 
## Which OSGi command returns an overview of both the REST and SOAP HTTP endpoints?
  
showendpoints
lrestdoc
listendpoints
**lendpoints**
 

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
 
## You create a SOAP service by using JMS as transport. One part of message is an attachment. The architect of your company requests for you to forward the message to a JMS Queue; however, you may only forward a reference to the attachment and not the attachment itself. What are the required steps to meet this request?
  
**In the SOAP Service Binding, set the persistence to file, and use the Get Context activity to obtain a reference to the file containing the attachment**
In the process implementation, write the attachment to file, and use the Get Context activity to obtain a reference to the file containing the attachment
In the SOAP Service Binding, set the persistence to file, and use the Read File activity to obtain a reference  to the file containing the attachment
In the process implementation, write the attachment to file, and use the output of the Write File activity  to obtain a reference  to the file containing the attachment
 
## You are required to create a SOAP HTTP Service. In the service implementation, you also need the transport context. Which steps are required to be performed in the process?
Create a schema for the HTTP Transport Context, and use the Set Context activity in the process
Create a Context Resource for the HTTP Transport context, and use the Get Context activity in the process
Create a Context Resource for the HTTP Transport context, and use the Set Context activity in the process
**Create a schema for the HTTP Transport Context, and use the Get Context activity in the process**


## You need to create a single REST service that has a Get Operation for an Employee resource. The resource has various fields, including FirstName, LastName, Age. Which resource service path should you provide to develop a single RESTful service that can use the partial response feature provided by Tibco ActiveMatrix BusinessWorks?
  
/employees?{field
/employees/{field?{ResponseType
/employees/{field
**/employees/field?{FirstName&{LastName&{Age**
 
## You want to test the sub-process in Tibco Business Studio. Which view allows you accomplish this?
  
BusinessWorks Jobs
Process view
**Process Launcher**
Console
 
## A Tibco ActiveMatrix BusinessWorks process encounters an exception and transitions into the exception handler routine. You need to implement processing in that routine and send the original exception to the higher scope?
  
**Rethrow**
Elevate
Repeat on Error
Throw

> Se invece il comportamento della gestione dell'errore tra processi padre/figlio (come lanciare l'errore)  
> Risposta: Throw
{.is-info}

 
## Which view of the Debug perspective in Tibco BusinessStudio displays the incoming and outgoing messages of an activity?
  
Variables
**Job Data**
Properties
BusinessWorks Jobs
 
## What are two methods for implementing the activity level error handling in Tibco ActiveMatrix BusinessWorks? (Choose 2 answers)  

Event Handlers
onError Activity
Conditional Transitions
**Error Transitions**
**Fault Handlers**
 
## By default, all projects that are open in Tibco BusinessStudio will be deployed when starting the debugger.
  
In the debug configuration, go to the Advanced tab, and deselect projects you do not want a debug
In the debug configuration, go to the Arguments tab, and add the argument –project
**In the debug configuration, go to the Applications tab, and deselect projects you do not want to debug**
In the debug configuration, go to the Enviroment tab, and deselect projects you do not want to debug
 


## There are two fault handlers. One Fault handler acts at the Scope Level, while the other fault handler is at the process level. What happens if the File Read activity throws a FileNotFoundException? ![capture.png](/certifications/bw6/capture.png)

**The Fault Handler surrounding the Read File Activity will be executed, and the Log Activity will be excecuted.**
Sono presenti due Fault Handler, uno Process Level e l’altro Scope Level. Nel caso in cui vada in errore il ReadFile, cosa viene eseguito?
Risposta: Anche se non è esposto nello screen e vengano nominati dei log non presenti, in primo luogo viene eseguito il fault handler dello Scope, dopo di ché se l’errore non viene gestito, va in esecuzione il Fault Handler del Process Level.

> (Sempre in riferimento allo screen) Cosa accade nel caso di errore del ReadFile2? (domanda molto simile con riferimento ad una activity non presente)
> Risposta: per quanto bisogni usare la fantasia, tra le risposte si fa riferimento ad un throw presente nel fault handler.
{.is-info}


## Which two statements are true about applications deployed to an AppSpace? (choose two)

Adding more appnodes will not affect capacity.
Adding appnodes after an application is deployed does not scale the application.
**Adding more appnodes will increase capacity.**
**A deployed application scales dynamically across all the appspace.**
A deployed application scales dynamically across all the appnode.

## What are the three minimum requirements for deploying  TIBCO Active Matrix BusinessWorks Applications across multiple machines? (Choose three)
  
Set up a domain with an AppSpace and an AppNode
Set up the deployment mode to enterprise by using the bwagent utility
**Set up a domain with at least one AppSpace and two AppNodes**
**Set up the deployment mode mode to enterprise by using the bwadmin utility**
**Set up the persistence store and communication transport layer for domain configuration data**
Set up a domain with deployment mode set to file system

## You are designing a transformation process, and your incoming data consists of a multiple repeating nodes of customer records. You need to filter and select customers belonging to a particular Region, which is representing by an element in the Customer Node Which configuration will carry out the filtering?
  
**A ‘for each’ loop with an ‘if’ loop nested underneath**
A ‘for each group’ loop with a ‘choice’ nested underneath 
A ‘choice’ loop with an ‘if’ loop nested underneath
An ‘if’ loop with ‘duplicates’ nested underneath
