---
title: XSD
description: Xml Schema Definition
published: true
date: 2021-02-10T13:16:54.217Z
tags: 
editor: markdown
dateCreated: 2021-02-07T14:56:02.960Z
---

# XSD

- **Goals**
1. XML Schema document: definition
2. Why using an XSD document
3. How to reference a XSD document from within a XML document
4. &lt;xs:schema> tag's attributes
5. Simple types 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Elements
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Attributes
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Constrains
6. Complex Types 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Elements
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Empty elements
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Types with only elements 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> d. Types with only text
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> e. Indicators (choice, sequence, all)
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> f. &lt;any> e &lt;anyAttribute> tags 
7. Include ed Import schema
---
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
		- **Union:** \<xs:union memberTypes=“typeName1 typeName2 ...”/>
		- **List:** \<xs:list itemType=“typeName”/>
			- Valid example with integer typeName: \<value>1 2 34 88\</value>
 		- **Restrictions:** facet or pattern-based restriction with a base type.
												\<xs:restriction base=“baseType”> ... </xs:restriction>
			- **Patterns:** \<xsd:pattern value=“regex”/>
				- Regex: (here “a” refers to a simple type)
					- Classics: a? , a+ , a* .
					- \[abcd]/(a|b|c|d)	→ 	a, b, c, d
					- \[a-z]			→ 	a, b, c, …, z
					- a{2,4}		→ 	aa, aaa, aaaa
					- \[^0-9]+		→ 	sequence of non digits
			- **Facets:** \<xs:facetName value=“...”/>
      
|         RESTRICTION         	|                                                            INFO                                                            	|
|:---------------------------:	|:--------------------------------------------------------------------------------------------------------------------------:	|
| enumeration                 	| Defines a list of acceptable values                                                                                        	|
| fractionDigits              	| Specifies the maximum number of decimal places allowed. <br>Must be equal to or greater than zero                              	|
| length                      	| Specifies the exact number of characters or list items allowed. <br>Must be equal to or greater than zero                      	|
| maxExclusive / minExclusive 	| Specifies the upper/lower bounds for numeric values excludingthe edge values.                                              	|
| maxInclusive / minInclusive 	| Specifies the upper/lower bounds for numeric values including the edge values.                                             	|
| maxLength / minLength       	| Specifies the maximum/minimum number of characters or list items allowed. <br>Must be equal to or greater than zero            	|
| totalDigits                 	| Specifies the exact number of digits. Must be greater than zero                                                            	|
| whiteSpace                  	| Specifies how white space (line feeds, tabs, spaces, and carriage returns) is handled. <br>(“replace”, “preserve”, “collapse”) 	|

- **COMPLEX ELEMENTS:** a complex element contains other elements and/or attributes.
												\<xs:complexType name="...">
	- **Definition:** \<xs:element name = “...”/>
										\<xs:complexType name=“elem”> ...Element Content... </…> </…>
	- **ANY:**	<xs:element name=“elem” type = “xs:anyType”/>
		- **\<any> Element:** allows us to extend the XML with unspecified elements.
													\<xs:any minOccurs="0"/> //Allows in its place anything or nothing.<<
		- **\<anyAttribute> Element:** allows us to extend the XML with unspecified attributes.
	- **EMPTY:** \<xs:element name=“elem” type = “xs:empty”/>
	- **Element Content:**
		- **SEQUENCE:** Sequence of elements (A, B, …).
									\<xs:sequence> elem1, elem2, ... </xs:sequence>
		- **CHOICE:** Choice of elements (A | B | ...).
									\<xs:choice> elem1, elem2, ... </xs:choice>
		- **SET/ALL:** Like a sequence but without constraints on the order .
									\<xs:all> elem1, elem2, ... </xs:all> 
			- If you also add minoccurs and/or maxoccurs you can also repeat the elements.
		- **CARDINALITY of elem1, elem2, ...:**  (DEFAULT is 1 for both min and maxOccur.)
			- A? → \<xs:element ... minOccurs= “0”/>
			- A+ → \<xs:element ... maxOccurs= “unbounded”/>
			- A* → \<xs:element ... maxOccurs= “unbounded” minOccurs= “0”/>
		- **COMPLEX CONTENT ELEMENT:** defines extensions or restrictions on a complex type that contains mixed content or elements only:

|                                                                                                                                                                                             EXTENSION                                                                                                                                                                                             	|                                                                                                                                                RESTRICTION                                                                                                                                                	|
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| \<xs:complexType name="fullpersoninfo"><br>  \<xs:complexContent><br>    \<xs:extension base="personinfo"><br>      \<xs:sequence><br>       \<xs:element name="address" type="xs:string"/><br>       \<xs:element name="city" type="xs:string"/><br>       \<xs:element name="country" type="xs:string"/><br>      </xs:sequence><br>    </xs:extension><br>  </xs:complexContent><br></xs:complexType> 	| \<product prodid="1345" /><br><br>\<xs:element name="product"><br>  \<xs:complexType><br>   \<xs:complexContent><br>     \<xs:restriction base="xs:integer"><br>      \<xs:attribute name="prodid" type="xs:int"/><br>     </xs:restriction><br>   </xs:complexContent><br>  </xs:complexType><br></xs:element> 	|

- **MIXED CONTENT:** “Mixed” attribute allows text between subelements.
	- \<xs:complexType name=“textType” mixed=“true”> ... \<xs:complexType/>
- **Translating XSD Languages to DTD:**
	- When 2 elements have the same name, DTD cannot distinguish them, thus **elements  and all non-shared attributes between the two become optional in DTD.**
	- **Approximations:**
		- Attribute types other than ID or IDREF are not understood, and become CDATA.
		- No distinction between synonymous elements.
		- Cannot declare who is the root of the document.

---

- **External Links**
[w3School XSD Schema Reference](https://www.w3schools.com/xml/schema_intro.asp)
- **Tools & Lab**
[Tool: Online XML - XSD formatter](http://www.freeformatter.com/)
[**Lab**: KP xsd exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfaEJXMktIQW5ROFE)