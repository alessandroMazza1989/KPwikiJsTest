---
title: XML
description: eXtensible Markup Language
published: true
date: 2021-02-05T18:12:32.913Z
tags: 
editor: markdown
dateCreated: 2021-02-05T18:05:11.602Z
---

# XML

- **Structure:** (XML is tree-structured)
	- **Prolog (optional):** defines the XML version and the character encoding: 
		\<?xml version="1.0" encoding="UTF-8"?>
	- **Root:**	\<root> ... \</root>
	- **Subelements:** \<element attribute="..."> ... \</element>
	- **Self-closing subelement:** \<subelement/>
	- **Comments:** \<!-- This is a comment -->

- **Case Sensitivity:** XML tags are case sensitive!
- **Entity References:** To use the five special characters of XML in different contexts use “\” or:
	-	<	→	\&lt;
	-	\>	→	\&gt;
	- &	→	\&amp;
	- ‘	→	\&apos;
	- “	→	\&quot;
- XML does not truncate multiple white-spaces
- The “xml” word, in any case-combination, is reserved.
- **Good Practice:** Use underscores for complex names. No dot or hyphens.
- **Using Attributes vs Elements:**
	- Prefer elements when saving DATA.
		- attributes cannot contain multiple values (elements can)
		- attributes cannot contain tree structures (elements can)
		- attributes are not easily expandable (for future changes)
	- Prefer attributes when storing METADATA about elements.
		- attributes are best suited to creating IDs with which to easily identify element tags.
- **The Omonimous Tags Problem:** how to differentiate omonimously tagged elements?
	- **Step 1:** Prefixes: for example: \<ns1:table> and \<ns2:table>
	- **Step 2:** Namespaces: prefixes must be defined within a namespace, so as to be reusable.
		- **Prefixed namespaces can be defined:**
			- With the **xmlns** attribute in the start tag of an element:
				<ns1:table xmlns:ns1="nameSpaceURL">
				\<ns1:element>
			- With the **xmlns** attribute in the XML root element:
				\<root xmlns:ns1="nsURL1" xmlns:ns2="nsURL2">
   	- **Default namespace** can be defined in context with an “empty” prefix:
    	\<table xmlns="defaultNameSpaceURL">
	- **Note:** Attributes can have prefixes too!
- **Escaped Text:** <[!CDATA[ ... ]]>

---
- **External Links**
[w3School XML Reference](http://www.w3schools.com/xml/)
[namespaces](https://www.html.it/articoli/il-misterioso-mondo-dei-namespaces/)
- **Tools & Lab**
Tool [Online XML - XSD formatter](http://www.freeformatter.com/)
