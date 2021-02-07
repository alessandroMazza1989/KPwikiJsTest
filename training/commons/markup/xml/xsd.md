---
title: XSD
description: Xml Schema Definition
published: true
date: 2021-02-07T14:59:25.500Z
tags: 
editor: markdown
dateCreated: 2021-02-07T14:56:02.960Z
---

# XSD

- **Uses:** XSD is a more advanced definition language than DTD for validating an XML document.
	- Unlike DTD, XSD is written itself in XML, so it’s extensible.
- **How to include:** by designating an XSD prefix and its relative namespace in the schema root.
	- <xs:schema xmlns:xs="XMLSchemaURI"> ... </xs:schema>
- **Example:**

|                                                                               DTD                                                                              	|                                                                                                                                                                                                                                                                                      XSD                                                                                                                                                                                                                                                                                      	|
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------:	|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| \<!ELEMENT note (to, from, heading, body)><br>\<!ELEMENT to (#PCDATA)><br>\<!ELEMENT from (#PCDATA)><br>\<!ELEMENT heading (#PCDATA)><br>\<!ELEMENT body (#PCDATA)> 	| \<?xml version="1.0"?><br>\<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"<br>targetNamespace="https://www.w3schools.com"<br>xmlns="https://www.w3schools.com"<br>elementFormDefault="qualified"> <br>\<xs:element name="note"><br>  \<xs:complexType><br>    \<xs:sequence><br>      \<xs:element name="to" type="xs:string"/><br>      \<xs:element name="from" type="xs:string"/><br>      \<xs:element name="heading" type="xs:string"/><br>      \<xs:element name="body" type="xs:string"/><br>    </xs:sequence><br>  </xs:complexType><br></xs:element><br></xs:schema> 	|

- **\<xs:schema> Attributes:**	
	- **xmlns:xs**					→ Custom namespace with prefix xs.
	- **targetNamespace**				→ Namespace of the schema’s elements 
	- **xmlns**						→ Default namespace
	- **elementFormDefault="qualified"**		→ All elements must be namespace qualified


