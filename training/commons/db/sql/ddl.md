---
title: SQL - DDL
description: Data Definition Language concepts
published: true
date: 2021-02-05T09:38:14.478Z
tags: 
editor: markdown
dateCreated: 2021-02-03T17:01:17.748Z
---

# Schema Creation

- CREATE SCHEMA [Name] [ [authorization] Auth ] {*SchemaElementDefinition*}

- A schema:
	- Contains: Domains, Tables, Indexes, Assertions, Views, Privileges.
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
|        Exact   Numeric       	|                      integer \| int \|   smallint                      	|                                                                      [(Precision [, Scale])]                                                                      	|         [AUTO_INCREMENT]         	|
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