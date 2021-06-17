---
title: Lista-Domande
description: 
published: true
date: 2021-06-17T13:23:35.221Z
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
