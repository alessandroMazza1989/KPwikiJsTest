---
title: XSD
description: Xml Schema Definition
published: true
date: 2021-02-07T15:10:27.450Z
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

- **How to reference a schema in an XML:**

|                                                                                                DTD                                                                                                	|                                                                                                                                    XSD                                                                                                                                    	|
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| \<?xml version="1.0"?><br>\<!DOCTYPE note SYSTEM ".../note.dtd"><br>\<note><br>  \<to>Tove\</to><br>  \<from>Jani\</from><br>  \<heading>Reminder\</heading><br>  \<body>Don't forget me!\</body><br>\</note> 	| \<?xml version="1.0"?><br>\<note xmlns="https://www.w3schools.com"<br>xmlns:xsi=".../XMLSchema-instance"<br>xsi:schemaLocation=".../xml note.xsd"><br>  \<to>Tove\</to><br>  \<from>Jani\</from><br>  \<heading>Reminder\</heading><br>  \<body>Don't forget me!\</body><br>\</note> 	|

- **ELEMENTS:** They represent an XML tag.
	- Definition by name uses the name “attribute”:
		\<xs:element name = “...” type = “xs:...” />
	- Definition by reference (ref) to another element:
		\<xs:element ref = “...” type = “xs:...” />
- **ATTRIBUTES:** They represent the attributes of the relative xml tag.
									\<xs:attribute name = “...” type = “xs:...” />
- **Default and Fixed Elements or Attributes:**
	- **Default:**	\<xs:el/attr name = “...” type = “xs:...” default = ”...” />
	- **Fixed:**		\<xs:el/attr name = “...” type = “xs:...” fixed = ”...” />
- **TYPES:** They represent the validation rule.
- **SIMPLE TYPES:** (No attributes or markup. Only #PCDATA or CDATA.)
	- **Types of Types:**
		- **Built-In:** string, normalizedString, token, boolean, integer, decimal, date, time, dateTime, duration, anyURI, ID, IDREF...
		- **User-Defined:** (Have the scope of the definition.)
			\<xs:simpleType name=“...”> ... </xs:simpleType>
	- **Type Derivation By:**
		- **Restrictions:** facet or pattern-based restriction with a base type.
			\<xs:restriction base=“baseType”> ... </xs:restriction>
			- **Facets:** \<xs:facetName value=“...”/>
      
|         RESTRICTION         	|                                                            INFO                                                            	|
|:---------------------------:	|:--------------------------------------------------------------------------------------------------------------------------:	|
| enumeration                 	| Defines a list of acceptable values                                                                                        	|
| fractionDigits              	| Specifies the maximum number of decimal places allowed. Must be equal to or greater than zero                              	|
| length                      	| Specifies the exact number of characters or list items allowed. Must be equal to or greater than zero                      	|
| maxExclusive / minExclusive 	| Specifies the upper/lower bounds for numeric values excludingthe edge values.                                              	|
| maxInclusive / minInclusive 	| Specifies the upper/lower bounds for numeric values including the edge values.                                             	|
| maxLength / minLength       	| Specifies the maximum/minimum number of characters or list items allowed. Must be equal to or greater than zero            	|
| totalDigits                 	| Specifies the exact number of digits. Must be greater than zero                                                            	|
| whiteSpace                  	| Specifies how white space (line feeds, tabs, spaces, and carriage returns) is handled. (“replace”, “preserve”, “collapse”) 	|

			- **Patterns:** \<xsd:pattern value=“regex”/>
Regex: (here “a” refers to a simple type)
Classics: a? , a+ , a* .
[abcd]/(a|b|c|d)	→ 	a, b, c, d
[a-z]			→ 	a, b, c, …, z
a{2,4}		→ 	aa, aaa, aaaa
[^0-9]+		→ 	sequence of non digits
Union: <xs:union memberTypes=“typeName1 typeName2 ...”/>
List: <xs:list itemType=“typeName”/>
Valid example with integer typeName: <value>1 2 34 88</value>