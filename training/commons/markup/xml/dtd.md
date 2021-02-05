---
title: DTD
description: Document Type Definition
published: true
date: 2021-02-05T18:29:25.183Z
tags: 
editor: markdown
dateCreated: 2021-02-05T18:29:25.183Z
---

# DTD

- **Uses:** A DTD defines the structure and the legal elements and attributes of an XML document. (Validation)
	- A well-formed XML document validated against DTD is both well-formed and valid.
- **How to include - The Doctype Directive:**
	- **Internal:**			\<!DOCTYPE typeName [DTD code...]>
	- **External:**			\<!DOCTYPE typeName SYSTEM “dtd file url”>
- **ELEMENTS:**
	- **Content Types:**
		- **Any:**			\<!ELEMENT elem ANY>
		- **Empty:**			\<!ELEMENT elem EMPTY>
		- **Simple (PlainText):**	\<!ELEMENT elem (#PCDATA)>
		- **Subelements:**		\<!ELEMENT elem (elem1, elem2, ...)>
		- **Mixed:**			\<!ELEMENT elem (#PCDATA | bold | asd)*>
	- **Content Definitions (Regular Expressions):**
		- **Sequence:**
			- **DTD:**		\<!ELEMENT elem (e1, e2, ...)>
			- **XML (ex):**	\<elem>	\<e1/>\<e2/>		\</elem>
		- **Choice (exclusive):**
			- **DTD:**		\<!ELEMENT elem a(b|c|d)>
			- **XML (ex):**	\<a> \<b>\</b> \</a>
		- **Iteration (Cardinality):**
			- **Single:**		\<!ELEMENT elem a(b)>
			- **Optional ?:**	\<!ELEMENT elem a(b?)>
			- **Repeating +:**	\<!ELEMENT elem a(b+)>
			- **Repeating *:**	\<!ELEMENT elem a(b*)>
- **ATTRIBUTES:**
	- **Structure:**			\<!ATTLIST elem 	attr1 type1 modifier1 attr2... >
	- **Types:**
		- **ID:** Unique identifier (key).	
			- Ex:		\<!ATTLIST elem attr ID #REQUIRED >
		- **IDREF(S):** Reference to an existing ID (like a foreign key).
			- Ex:		\<!ATTLIST elem attr IDREF #REQUIRED >
		- **NMTOKEN(S):** A char string (or list) with no spaces or separators.
		- **ENTITY(IES):** Value obtained by expansion of an entity (not seen here).
	- **Modifiers:**
		- **“default”:** 		Expressed with a string. Default value if attribute is not set.
		- **#FIXED val:**  	Attribute must assume that value.
		- **#REQUIRED:**		Attribute must be specified.
		- **#IMPLIED:**		Attribute is optional. If Type is ID it creates a new unique ID.
- **ENTITIES:** (Recurrent fragments of text that are expanded at parsing.)
	- **Structure:**			\<!ENTITY entityName value>
	- **Referencing:**			&entityName;
- **INTERSECTION OF LANGUAGES:** every element’s definition is analyzed locally, so for alle the intersection of 2 elements they need to have the same components defined in the same way for them to be kept in the intersection, regardless of what they refer to.
- Unfortunately DTD is not written in XML and we can’t describe/validate DTD with DTD, unlike with XSD.
