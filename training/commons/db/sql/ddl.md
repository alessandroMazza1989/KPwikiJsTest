---
title: SQL - DDL
description: Data Definition Language concepts
published: true
date: 2021-02-05T14:51:26.928Z
tags: 
editor: markdown
dateCreated: 2021-02-03T17:01:17.748Z
---

# Schema Creation

- CREATE SCHEMA [Name] [ [authorization] Auth ] {*SchemaElementDefinition*}

- A schema:
	- **Contains:** Domains, Tables, Indexes, Assertions, Views, Privileges.
	- Has a Name and Owner.

# Domains

- Specify what types of values are allowed in the attributes.
- There are 2 types: Elementary and User-defined.

## Elementary Domains

|            DOMAIN            	|                                  TYPE                                  	|                                                                              OPTIONS                                                                              	|               INFO               	|
|:----------------------------:	|:----------------------------------------------------------------------:	|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------:	|:--------------------------------:	|
|    Characters 	|                          character [varying]                           	| [(Length)] [ character set Family]                                                                                                                                	| varying means variable   length. 	|
|          Characters          	|                                  char                                  	| [(Length)] [ character set Family]                                                                                                                                	| varying means variable   length. 	|
|          Characters          	|                                 varchar                                	| [(Length)] [ character set Family]                                                                                                                                	| varying means variable   length. 	|
|              Bit             	|                            bit   [varying]                             	| [(Length)]                                                                                                                                                        	| varying means variable   length. 	|
|              Bit             	|                                 varbit                                 	| [(Length)]                                                                                                                                                        	| varying means variable length.   	|
|         Exact Numeric        	|                                 numeric                                	| [(Precision [, Scale])]                                                                                                                                           	|                                  	|
|        Exact   Numeric       	|                                 decimal                                	| [(Precision [, Scale])]                                                                                                                                           	|                                  	|
|        Exact   Numeric       	|                      integer \| int \|   smallint                      	|                                                                      [(Precision [, Scale])]                                                                      	|         [AUTO_INCREMENT]^1^         	|
|     Approximate   Numeric    	| float [(Precision)]                                                    	|                                                                                                                                                                   	|                                  	|
|     Approximate   Numeric    	| real                                                                   	|                                                                                                                                                                   	|                                  	|
|     Approximate   Numeric    	| double precision                                                       	|                                                                                                                                                                   	|                                  	|
|         Time Instants        	| date (fields month, day, year)                                         	|                                                                                                                                                                   	|                                  	|
|        Time   Instants       	| time [(Precision)] [with time zone] : (fields hours, minutes, seconds) 	|                                                                                                                                                                   	|                                  	|
|        Time   Instants       	| timestamp [(Precision)] [with time zone]                               	|                                                                                                                                                                   	|            YYYY-MM-DD            	|
|        Time Intervals        	|                    interval timeUnit1 [to timeUnit2]                   	| Units can be different, but must be in these 2   sets: (year, month) and (day, hour, minute, second). That’s because months   don’t have the same number of days. 	|                                  	|
|            Others            	| Boolean                                                                	|                                                                                                                                                                   	|                                  	|
|            Others            	| Bigint                                                                 	|                                                                                                                                                                   	|                                  	|
|            Others            	|                                  BLOB                                  	|                                                                                                                                                                   	| Binary Large Object              	|
|            Others            	|                                  CLOB                                  	|                                                                                                                                                                   	| Character Large Object           	|
|                              	|                                                                        	|                                                                                                                                                                   	|                                  	|
|                              	|                                                                        	|                                                                                                                                                                   	|                                  	|

---
^1^ **SERIAL** in PostgreSQL

## User-Defined Domains

- CREATE DOMAIN DomainName as DataType [default <GenericValue|user|null>] [Constraints]

- Default values: 
	- **GenericValue:** can be a value compatible with the domain, like a constant or an expression.
	- **user:** the login user name of the user that issues the command
	- **null:** is the polymorphic value null
  
## Table Creation, Deletion, Clearing
### CREATE, DROP, TRUNCATE

|                                                                   COMMAND                                                                  	|                                                     INFO                                                     	|
|:------------------------------------------------------------------------------------------------------------------------------------------:	|:------------------------------------------------------------------------------------------------------------:	|
| CREATE TABLE TableName (<br>    AttributeName AttributeType [DefaultValue] [AttributeConstraint],<br>    ...,<br>    TableConstraints<br>) 	|                                                                                                              	|
| DROP TABLE TableName cascade                                                                                                               	| It’s always prudent to use cascading option with deletion.                                                   	|
| TRUNCATE TABLE TableName                                                                                                                   	| Erases all memory of the table leaving only its structure, making it as new and resetting auto-incrementers. 	|

# Constraints

- Can be expressed in two ways:
|                   COMMAND                   	|                          INFO                         	|
|:-------------------------------------------:	|:-----------------------------------------------------:	|
| ElementName ElementType Constraint          	| Inline with declaration.                              	|
| Constraint(ElementName1, ElementName2, ...) 	| As a separate assertion at the end. Batch definition. 	|

## Constraints Within Relations

|      KEYWORD      	|                                           INFO                                          	|
|:-----------------:	|:---------------------------------------------------------------------------------------:	|
| NOT NULL          	| Imposes that the field cannot be null.                                                  	|
| UNIQUE            	| Makes element unique. Defines possible key candidates.                                  	|
| PRIMARY KEY       	| Defines primary key. <br>⚠️Only one (set) per table! <br>⚠️Implies not null! Can also be foreign. 	|
| CHECK (Condition) 	| Checks if a particular property is satisfied.                                           	|

- **Example:**
	- CREATE TABLE Employee(
  ID CHAR(6) PRIMARY KEY,
  Name VARCHAR(20) NOT NULL,
  Surname VARCHAR (20) NOT NULL,
	Pay FLOAT DEFAULT 0.0,
	Supervisor CHAR(6) CHECK (ID LIKE “1%”^2^ OR Department in (SQLquery...)),
	UNIQUE(Name, Surname));
  
---
^2^ Like checks if it satisfies the regular expression. The 1% means “any set of characters after 1”

## Constraints Between Relations
### Referential Integrity

|           KEYWORD           	|                                  INFO                                 	|
|:---------------------------:	|:---------------------------------------------------------------------:	|
| FOREIGN KEY                 	| Declares the element as referencing another table.                    	|
| REFERENCES Table(Attribute) 	| Declares the reference to another table. <br>⚠️Implies it’s a FOREIGN KEY. 	|

- ⚠️The Master Table’s attribute that is referenced must also be UNIQUE (or a PRIMARY KEY)!
- ⚠️If an attribute is a PRIMARY KEY it can already act as a FOREIGN KEY, so there’s no need to declare it as such. It will still need the REFERENCES constraint if it is referenced, however.
- ⚠️A separate REFERENCES statement is necessary for each external table!

- **Example:**
	- CREATE TABLE Employee( 
		ID CHAR(6) PRIMARY KEY,
		Name VARCHAR(20) NOT NULL, Surname VARCHAR (20) NOT NULL,
		DepartmentName VARCHAR (15) REFERENCES Department(DepartmentName),
		FOREIGN KEY(Name, Surname) REFERENCES Registry(Name, Surname) );

## Constraints Defined Outside
### Assertions

- CREATE ASSERTION AssertionName check (Condition)

## Conditions

- Some special conditions can be: 
	- EXISTS SQLQuery, NOT EXISTS SQLQuery, Attr LIKE “string[%]”, … 
  
## Constraint Violations
### Internal Table Violations (Slave)

- Violations that introduce values in a Slave Table that have no counterpart in the Master Table.
- Such violations can occur when:
	- Updating the value of an attribute that references another table’s attribute.
	- Adding a new line.
- Such operations are simply blocked.

### External Table Violations (Master)

- Such violations occur when the external table (the table with the “original” values) is edited in these two ways:
	- **ON UPDATE:** when a referenced attribute is modified.
	- **ON DELETE:** when a referenced row is deleted.

### Violation Management Policies

|   KEYWORD   	|                                                                                                 INFO                                                                                                 	|
|:-----------:	|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| CASCADE     	| - if ON UPDATE: All internal tables’ values are updated with the new value. <br>- if ON DELETE: All corresponding internal tables’ rows are also deleted.<br>(Use when inbound cardinality is (0,n)) 	|
| SET NULL    	| All internal tables’ attributes that reference this one are set to null, regardless of deletion or update.                                                                                           	|
| SET DEFAULT 	| All internal tables’ attributes that reference this one are set to their default values, regardless of deletion or update.                                                                           	|
| NO ACTION   	| Update or deletion are blocked. (Use when inbound cardinality is (1,n))                                                                                                                              	|

- **Example:**
	- CREATE TABLE Employee( 
		ID CHAR(6) PRIMARY KEY,
		Name VARCHAR(20) NOT NULL,
		Surname VARCHAR (20) NOT NULL,
		DepartmentName VARCHAR (15) REFERENCES Department(DepartmentName),
		FOREIGN KEY(Name, Surname) REFERENCES Registry(Name, Surname)
		ON DELETE CASCADE,
		ON UPDATE NO ACTION );

## Schema Modification
### ALTER TABLE


|                         COMMAND                        	|                  INFO                 	|
|:------------------------------------------------------:	|:-------------------------------------:	|
| ALTER TABLE TableName ADD ColumnName DataType          	| Adds a column to the table.           	|
| ALTER TABLE TableName DROP COLUMN ColumnName           	| Deletes a column (Cascading required) 	|
| ALTER TABLE TableName ALTER COLUMN ColumnName DataType 	| Edits a column (Cascading required)   	|

## Views
### CREATE VIEW

- They offer a virtual table defined by a query. 
- They can be queried themselves, which also allows the creation of views from other views.
- Editing them edits the relative values in the original tables, assuming the edit does not create ambiguities.
	- ⚠️However, applying edits directly on views is NOT RECOMMENDED!!! 
  
|                                                  COMMAND                                                 	|                                                                                                         INFO                                                                                                        	|
|:--------------------------------------------------------------------------------------------------------:	|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| CREATE VIEW ViewName [(AttributeList)] as <br>    SQLQuery <br>    [with [local\|cascaded] check option] 	| - check option: intervenes when a view’s content is updated by verifying the consistency of the update.<br>- local: check is performed only on this view. <br>- cascaded: check is performed on all related views.  	|


- **Example:**
	- CREATE VIEW Client7Orders as 
		select *
		from Orders
		where ClientID = ‘7’
		with local check option
