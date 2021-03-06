---
title: Development - Questions
description: 
published: true
date: 2021-06-10T11:25:38.565Z
tags: 
editor: markdown
dateCreated: 2021-06-07T10:39:20.487Z
---


# Development

## Which three steps are correct for developing BusinessWorks solutions? (Choose three)

a. **Test and Debug**
b. Deploy EAR
c. Define Domain
d. **Define Processes**
e. Upload EAR
f. **Add Modules**

# Conversations

## In un processo che consiste nella gestione degli ordini, come gestire la cancellazione dell'ordine e garantire il rollback di tutte le azioni

Risposta: **Conversation**

## **You need to cancel an online order and ensure the money is returned to the customer. Which method in TIBCO AM BW allows you to most effectively manage, execute, or revert a Unit Of Work so that you can achieve this goal?**

Define an error handler in a scope.
**Define a conversation.**
Define an error transition.
Define a repeat on error activity

## Un utente che ha aggiunto un oggetto nel carrello, deve annullare l’ordine e cancellarlo. Come fai a far in modo che ciò possa avvenire?

Risposta: tra le risposte era presente **Conversation**

## You need to design a TIBCO AM BW Process so that you maintain the context from previous processes instance. Which feature should you use?

dialogues
shared variables
**conversations**
context variables

# Mapper

## You are using a Mapper activity in your process design. Which three can be used as inputs in the Mapper Input tab? (Choose three.)

**Primitive Datatype**
Database Resultset
DTD File
**Inline Schema**
**Complex Datatype**
CLOB

## Which three types of elements are used by Variables in Mapper activity? (Choose three)

a. **Primitive**
b. **Inline Schema**
c. **Complex**
d. Structure
e. Java

## Mapper come settare i valori del process context in un mapper

Risposta: Nessuna impostazione di default il mapper ti consente di farlo

## Come gestire il process context all'interno di un Mapper?

Risposta: è di default presente nel Mapper

## Quando posso mappare il processContext in un mapper?

nel mapper è sempre possibile mapparlo oppure Nessuna impostazione di default il mapper ti consente di farlo

## Come selezionare in un Mapper da un data source con elementi ripetitivi del tipo Customer solo i customer di una specifica location:

Risposta: XPATH expression 

		<customer>
 		<location>…\</localtion>
		</customer>
		.
		<customer>
 		<location>…\</localtion>
		</customer>

Foreach nodo customer + if annidato (if location='Roma'): for-each customer[location="Roma"]

## Qual è la condizione minima per poter utilizzare in input ad un Mapper l'output di un'activity precedente?

Risposta: impostare uno schema nell’ input tab del mapper

## What is the minimum requirement for mapping the output of a preceding activity to the input of a mapper?

Define a data element in the input tab of the preceding and Mapper activity
**Define a data element in the input tab in the Mapper activity**
Define an output data element  of the Mapper activity
Define a data element for the input of a preceding activity

            
## Come si implementa uno switch case su un mapper.

Risposta: surround with choose

## Which configuration is required to implement a switch case in a mapper activity within a process flow?

Repeatitive Group
Surround With Scope
**Surround with Choice**
Non-Repeatitive Group

## Per un qualche motivo una plugin function è andata in errore nell’input di un mapper. Devi disinstallarla.

Risposta: le opzioni sono “eliminazione in application, application module, file>disinstalla plugin fragmenr, help>tibco help

# XPATH / XSLT / XML

## Come esportare da un progetto un Custom Xpath e importarlo su un altro progetto?

Risposta: Plug-in Development/Deployable Plug-ins and fragments + Install into .host Repository

## A Custom xPath function has been created in a TIBCO AM BW Project. How can the function be made available (at design time) to other project? (Choose two)

**by installing it into host repository deployable plug-ins and fragments.**
**by exporting the deployable plug-ins and fragments.**
by exporting the custom xpath function resource
by installing the Custom xpath function into TIBCO AM BW target project
by adding the custom Xpath function to a target project

## Custom XPath functions. Come si disinstalla una custom function a design-time?

Risposta: disinstalla il deployable fragments and plugin (qualcosa del genere)

## A custom XPath function associated with mapper activities in Active Matrix BusinessWorks processes ..deprecated. How can the custom XPath function be removed from the mapper?
 
Uninstall the custom XPath function from the application module
Uninstall the custom XPath function plug-in from the application project
**Uninstall a custom XPath function by using Help > About Tibco ActiveMatrix BusinessWorks Menu**
Uninstall a custom XPath function by using File > Tibco ActiveMatrix BusinessWorks Menu

## You are migrating an application, which includes some custom XPath functions. Which runtime task is needed to make the custom function available?

Risposta: Include the XPath function plug-ins in your application.

## You are migrating an application, which includes some custom XPath functions. Which runtime task is needed to make the custom function available?
 
Include the custom XPath function plug-ins into the Host repository.
Export the XPath function as a zip, and import it through BusinessStudio.
Export the XPath function as a jar, and update the bwagent path.
**Include the XPath function plug-ins in your application.**

## Il cliente mi da un XSLT da utilizzare. Con quale activity implemento questa cosa?

Risposta: XML Transform

## Quale Activity viene utilizzata se un provider ti fornisce un XSLT per formattare il proprio msg RISP?

Risposta: XML Activities Palette🡪 XML Transform

## You have a situation in which an external source supplies an XSLT file to perform the trasformation, and you want to leverage the file. Which activity helps you accomplish this goal?

Mapper
**Transform XML**
Invoke XSLT
Render XML

## What are five supported options for XML to JSON conversion? (Choose five)

a. **Normal Conversion**
b. JSON String to XML String
c. **JSON Document to XML Document**
d. **Badgerfish Conversion**
e. **XML String to JSON Document**
f. **XML String to JSON String**

# Transitions

## Quando hai una transaction with condition cosa viene soddisfatto?

Risposta: XPATH expression

## Su una transaction with condition quando passava il flusso?

quando l'espressione dell'xpath è true

## What kind of expression is used to build the condition? 

It's an XPATH expression. Transition with condition

# Compensation / Error / Handlers 

Compensation (tre domande) che succede in caso di eccezioni all'interno dello scope nel processo mostrato

Viene mostrato questo processo 

![image.png](/certifications/bw6/image.png)

La domanda è posta male perché non ti fa vedere tutto il processo e indica nomi sbagliati delle palette.

### Cosa succede quando l’ultimo ReadFile va in errore?

Risposta: Nel processo è incluso il Fault Handlers con un’activity di Compensate. L’ultimo ReadFile va in errore, quindi entra nel Fault Handler che lancia la compensation dello scope, quindi viene loggato il CompensationLog

### (Tenendo conto sempre dell’immagine) Sono presenti due Fault Handler, uno Process Level e l’altro Scope Level. Nel caso in cui vada in errore il ReadFile, cosa viene eseguito?

Risposta: Anche se non è esposto nello screen e vengano nominati dei log non presenti, in primo luogo viene eseguito il fault handler dello Scope, dopo di ché se l’errore non viene gestito, va in esecuzione il Fault Handler del Process Level.

### (Sempre in riferimento allo screen) Cosa accade nel caso di errore del ReadFile2? (domanda molto simile con riferimento ad una activity non presente)

Risposta: per quanto bisogni usare la fantasia, tra le risposte si fa riferimento ad un throw presente nel fault handler.

## There are two fault handlers. One Fault handler acts at the Scope Level, while the other fault handler is at the process level. What happens if the File Read activity throws a FileNotFoundException? (vedi disegno precedente) 

The Fault Handler surrounding the Read File Activity will be executed, and the Log Activity will be excecuted.

## In quanti modi si può gestire un error? (Seleziona 2)

Risposta: Fault Handler e Error Transition

## What are two methods for implementing the activity level error handling in Tibco ActiveMatrix BusinessWorks? (Choose 2 answers) 

Event Handlers
onError Activity
Conditional Transitions
**Error Transitions**
**Fault Handlers**

## In che modo puoi continuare ad eseguire un processo nonostante si presenti un errore?

Risposta: Transition with Error

## Come gestire l'errore da una activity senza far scattare l'error handler	

Risposta: Con la transaction on "Error"

## Verificare il comportamento della gestione dell'errore tra processi padre/figlio (come lanciare l'errore) 

Risposta: Throw

## Come rilanciare lo stesso errore generato in un subprocess al chiamante

Risposta: Rethrow

## A Tibco ActiveMatrix BusinessWorks process encounters an exception and transitions into the exception handler routine. You need to implement processing in that routine and send the original exception to the higher scope?

**Rethrow**
Elevate
Repeat on Error
Throw

## Se invece il comportamento della gestione dell'errore tra processi padre/figlio (come lanciare l'errore) 

Risposta: Throw

## Where can a fault handler be attached in a process? (Choose two.)

Risposta: Process Level e Scope Level 

## Where can a fault handler be attached in a process? (Choose two.)
 
Service Binding Level
**Process Level**
**Scope Level**
Reference Binding Level
Application Module Level

## You need to define an Event Handler for asynchronous processing for a given process. At which levels can you create an event handler?

Scope Level and Activity Level
**Scope Level and Process Level**
Module Level and Process Level
Activity Level and Process Level

## In which scope would you place a Rethrow activity?

**Fault Handler**
Compensation Handler
Transaction Scope
Event Handler

# Shared module

## Quali elementi di uno shared module sono visibili dagli altri moduli:

Risposta: Public processes e Shared Resources

## Che tipo di risorse possono essere chiamate da uno Shared Module

Risposta: Public Process e Shared Resource

## Which two shared module functionalities are exported to the application and other shared modules? (Choose two)

**Shared Resources**
Private processes
Service Bindings
**public processes**
reference bindings

# Log

## Quale livello del log di default per un appnode?

Risposta: Info

## What is the default setting for the log level of an AppNode log file?

**ERROR**
INFO
WARN
DEBUG

Riferimento: https://docs.tibco.com/pub/activematrix_businessworks/6.3.1/doc/html/GUID-FCC52408-0859-4C22-966C-0AB7B7463903.html

## What is the default logging level for bwagent and bwadmin?

a. **INFO**
b. DEBUG
c. TRACE
d. ERROR
R: a

# Groups

## Quale gruppo ti consente di elaborare tutti i membri estratti da una query

Risposta: Iterate.

## If you need the loop through every User record in a database, which scope should you use?

**Iterate**
PichFirst
If
RepeatOnError

## A TIBCO AM BW application has to post a transaction by calling an external Web Service. The business Requirment is to attempt the call to web service at least three times if the service is not available Which group type can be used for this scenario?

ForEach
Iterate
Repeat
**RepeatOnError**

## Which type of loop has a simple index variable that counts each iteration and has a conditional expression to determine when to stop?

a. While
b. Iterate
c. For-Each
d. **Repeat**

# WSDL

## wsdl con due operation qual è il miglior modo per implementare entrambe?

Risposta: utilizzo 2 constructor (1 per ogni operation) nello stesso processo

## You are given a WSDL has two distinct operations in a single Port Type. You need to implement this WSDL by using TIBCO AM BW. What should you do?

Create a single process, and use a recive activity for both operations.
Create two applications that implement both operations, and set the activation mode to single.
**Create a single process, and use a constructor for both operarions.**
Create two processes, and remove one operation in both processes.

## Attachement in WSDL. Di che tipo sono definiti, definito come mimepart del multipart.

Risposta: In this configuration, a part of the input or output WSDL message of type base64binary is configured as an attachment. In a concrete WSDL, the attachment is described as a mime part of the multipart message.

## Di cosa ha bisogno un process service per esporre le operazioni?

Risposta: **WSDL**

# Resources

## Non vengono mostrate le risorse JDBC. Da cosa può dipendere?

Risposta: JDBC Connection si trova in un altro shared module
Risposta Stefano: JDBC Connection si trova in un altro application module

## While configuring a JDBC Query activity, the JDBC Connection does not show up in the resource list. What is the issue?

The JDBC Connection was configured in JAVA Module.
The JDBC Connection was configured in the current Application Module.
The JDBC Connection was configured in a different Shared Application Module.
**The JDBC Connection was configured in a different Application Module.**

## Matching tra Risorse e attività che si vuole eseguire. Esempio mandare una mail à SMTP Server

## Select the appropriate shared resource to associate with the task:

Transfers email messages between servers SMTP Resource **[STMP Resource]**
Contains the specification for parsing or rendering a text string **[Data Format]**
Represents an outgoing HTTP connection with a SOAP binding  **[HTTP Client]**
Provides a way to configure the JNDI provider for a JMS Connection **[JNDI Configuration]**

## One question was to associate the shared resource from a dropdown menu to each statement, with 4 options in the dropdown.

For instance :

## Update a db table, Options : SMTP,HTTP CLIENT,JNDI Conf,JDBC Conn . 

The right one is JDBC

## Send a mail,  Options(from a dropdown) : SMTP,HTTP CLIENT,JNDI Conf,JDBC Conn . 

The right one is SMTP

## While designing applications, if you wish to use the same JMS Connections Resource in multiple application modules, where should you configure it?

Plug-in
**Shared modules**
Application
Application modules

# Variables / Properties

## Matching tra Module Shared Variables e Job Shared Variables
Risposta: vengono presentate 4 situazioni e bisogna selezionare in 3 casi le Module Shared Variables ed in 1 caso la Job Shared Variable
## Come si passa il context ad altri process instances?
Risposta: Shared variables
## A large data set needs to be passed from a parent to multiple inline child processes. The variable has to be visible to processes across different modules. Which variable is correct to use in this situation?
Risposta: job shared variables
## A large data set needs to be passed from a parent to multiple inline child processes. The variable has to be visible to processes across different modules. Which variable is correct to use in this situation?
 
substitution variables
module shared variables
application shared variable
**job shared variables**

## 4 casi mostrati. Da definire se usare una module shared variable o una job shared variable.

## You have a scope variable within a scope, and you want to override a process variable. Which activity allows you to override the process variable?

Mapper Activity
**Set Shared Variable Activity** Possibile Risposta
**Assign Activity**  Possibile Risposta
Get Shared Variable Activity
## Da uno scope come sovrascrivere una shared Variable

ho risposto utilizzando Set Shared Variable, nel caso di process variable dovrebbe essere assign)
## There were different questions with this dropdown menu and I think each option has to be selected once. For instance in a similar question on shared variables, there were 4 options in the drop down menu but 3 options were
Sequenza risposta (module shared variable,module shared variable,module shared variable, job shared variable).

## Which statement is true about Properties scope?

a. A property defined at the parent layer can reference a property defined in the inner layer
b. An application property can reference a process property
c. **A process property can reference a module property**
d. A module property can reference an activity configuration property

## Which two statements are true about properties? (Choose two)

a. An application property can reference a process property
b. **A process property can reference an application property**
c. **A module property can be injected into a process activity**
d. A module property can reference an application property

# Coercion
## In quale caso si usa la Coercion? (Studiare)
https://docs.tibco.com/pub/businessevents-express/5.2.1/doc/html/GUID-CB4EF185-D1CE-4C90-A321-826D0293F82B.html
## In which of the following cases should you use Coercion in a Mapper Activity?
**When the input data type is unknown, and the output data type is know.**
When the input data is repeating, and the output data is not.
When the input data is not repeating, and the output data is repeating.
When the input data type is known, and the output data type is unknown.

# Critical section
## Come posso sincronizzare i process instance che contengono Critical Section.
Risposta: Uso una Shared Lock variable di modulo.
## Situazione con una Critical Section.
Risposta: tra le risposte è presente Shared Lock Variable
## You need to synchronize multiple Critical Section groups that can be part of different process instances. What should you do to accomplish this goal?
Increase the Timeout of the Critical Section to allow for all the different process instance to synchronize.
**Create a Shared Lock in your Critical Section with a Module Shared Variable as Shared Variable Type.**
Change the Group Type from Critical Section to Local Transaction.
Create a Shared Lock in your Critical Section with a Job Shared Variable as Shared Variable Type.

# Palettes / Activities
## Which activity allows you to collect multiple transition flows to resume a single flow of execution in the process?
Risposta: Empty activity
## Which activity allows you to collect multiple transition flows to resume a single flow of execution in the process?

a.	**Empty activity**
b.    Null activity
c.    Exit activity
d.    Scope activity
## Quali sono le activities che hanno la local transactional capability?
Risposta: JMS e JDBC
## Which two types of activities have transactional capabilities in ActiveMatrix BusinessWorks? (Choose two).  
a.      Java activities
b.      **JMS activities**
c.      Rendezvous activities
d.      SOAP activities
e.      **JDBC activities**

https://docs.tibco.com/pub/activematrix_businessworks/6.3.1/doc/html/GUID-9402B865-0302-40B6-9D7B-B4A173D4E314.html
## Quali sono le palette di start? (scegli 2)
Risposta: (Elenco di palette da scegliere tra Signal-In, Wait, etc…)
## Which two Adapter Palette activities are Process Starters? (Choose two.)

Receive Adapter Request
**Adapter Request-Response Server**
**Adapter Subscriber**
Send Adapter Response
Wait for Adapter Request

## Which type of activity is require to implement an asynchronous event in a running process and the ….executing the process instance when an appropriate event is received?

Event handler activity
Process Starter activity
Regular activity
**Signal-in activity**
## Domanda su paletta Rendezvous

## During development, one of your peers asks you for help on how to call an external …..Which activity should you recommend that they use?

Invoke API activity
**Invoke activity**
HTTP Request/Response activity
SOAP Request/Reply activity

## Which tool provides JDBC Query Execution at design time?

a. Database Perspective
b. Scrapbook
c. Shared JDBC Resource
d. **Database Browser**

# Debug
## While debugging an application inside TIBCO BusinessStudio, when is the job data visible in the job data view?
Risposta: after selecting an activity in a job
## While debugging an application inside TIBCO BusinessStudio, when is the job data visible in the job data view?
 
**after selecting an activity in a job**
after selecting an activity in completed jobs only
a Process Definition that implements the operations of the service
after selecting a completed job
after selecting the job data view
## Durante il debug tutti i processi verranno debuggati di default. (la domanda era più o meno così e non poneva condizioni, tuttavia si capisce dalle risposte che vuole sapere in che modo si possa evitare di debuggare tutti i processi)
Risposta: Debug configuration>application – deselezionare i processi che non si vogliono debuggare
## By default, all projects that are open in Tibco BusinessStudio will be deployed when starting the debugger.

In the debug configuration, go to the Advanced tab, and deselect projects you do not want a debug
In the debug configuration, go to the Arguments tab, and add the argument –project
**In the debug configuration, go to the Applications tab, and deselect projects you do not want to debug**
In the debug configuration, go to the Enviroment tab, and deselect projects you do not want to debug
## Dove puoi vedere il contenuto dei messaggi delle activity in input ed output durante il debug?
Job Data
## Which view of the Debug perspective in Tibco BusinessStudio displays the incoming and outgoing messages of an activity?

Variables
**Job Data**
Properties
BusinessWorks Jobs
## Which two options are available for debugging an application remotely in Business Studio? (Choose two) 
a. **Edit processes**
b. **Set breakpoints**
c. View job and shared variables
d. Edit properties

# Processes
## You need to define a process that can only be invoked by other processes that are a part of the same package. Which modifier should the process have?
Risposta: private

Public: can be invoked by processes that are defined either inside or outside the package.

Private: can be invoked only by processes that are part of the same package.
## You need to define a process that can only be invoked by other processes that are a part of the same package. Which modifier should the process have?
public
static
**private**
protected

## What should you configure in order to define Startup Process tasks for a given application?

Startup Process
Main Process
Initiator Process
**Activator Process**

## Process Activation

Activation mode for a process defines the way in which processes are activated at runtime.
- Multiple AppNodes: At runtime, the application is distributed and activated on all the AppNodes in the AppSpace. In the event of a failure on one of the AppNodes, the application continues to run with fewer AppNodes.
- Single AppNode: At runtime, the application is activated on only one AppNode in the AppSpace. In the event of a failure, another AppNode will be activated and any check pointed data can be recovered.

# JMS

## You are defining a process that uses the JMS Send Message activity to send a message to a backend application. this application replies asynchronously and does not maintain the other of messages. Which activity should you use if you need to correlate the replies from this application back in your original process?

Wait for JMS Request
JMS receive message
Get JMS queue message
**JMS Request Reply**

# Checkpoints
## Domanda su checkpoint e job

## Which three statements are true for using Checkpoints with Transaction? (Choose three)
a. When a checkpoint occurs in a non-inline sub-process, it saves the state of the parent process instance only
b. **JTA and XA transaction group can configure a built-in checkpoint**
c. **Each process instance keeps only its most recent checkpoint data**
d. **When a checkpoint occurs the process data and state can be saved to file or database**

# Breakpoints

## When can break points be set?

a. **Either when the engine is running or the engine is stopped**
b. Only when the engine is running
c. Only in design time environment
d. Only when the engine is stopped

# Query

## Which three features are supported by Query Builder? (Choose three)

a. **Execute and Test**
b. **Select Statement Type**
c. Create Stored Procedure
d. Execute Triggers
e. **Add Conditions and Groups**

# Packages

## A TIBCO ActiveMatrix BusinessWorks process is defined in a package. What is a package equivalent to?

a. A project
b. An application
c. A workspace
d. **A folder**
e. A module

# Perspectives

## A TIBCO Business Studio perspective is a set of …

a. **views**
b. palettes
c. wizards
d. pictures


# Application modes
## Activation mode delle application
 sorgente: https://docs.tibco.com/pub/activematrix_businessworks/6.2.1/doc/html/GUID-996BD718-B56D-461F-89EF-7D93D0F088AC.html

## What is the activation mode when BusinessWorks 6.x application is deployed using non-managed fault tolerance?

a. **Active-Active**
b. Passive-Active
c. Passive-Passive
d. Active-Passive




