---
title: XSLT
description: eXtensible Stylesheet Language Transformations
published: true
date: 2021-02-10T13:23:25.921Z
tags: 
editor: markdown
dateCreated: 2021-02-08T13:20:22.556Z
---

# XSLT

- **Goals**
1. XSLT document definition
2. &lt;stylesheet> and &lt;transform> elements
3. &lt;template> element
4. &lt;value-of> element
5. &lt;for-each> element
6. &lt;sort> element
7. &lt;if> element
8. &lt;choose> element
9. &lt;apply-templates> element

---

- Used to transform an XML document into another XML document (usually an HTML, but not necessarily). 
- **Style Sheet Declaration:** \<xsl:stylesheet> or \<xsl:transform>
															\<xsl:stylesheet 	version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
- **Elements:**
	- **The template element:** 	\<xsl:template match="XPATH_expression">
		- It’s used to build templates.
		- **The match attribute:** is used to associate a template with an XML element, or with the entire document (“/”). It’s an XPATH expression.
	- **The apply-templates element:** \<xsl:apply-templates [select]="XPATH_expr">
		- Applies a template rule to the current element or to the current element's child nodes.
			- This means that it can be substituted in a way to a for-each, as it automatically iterates, 				depending on the selection, on all the child nodes.
			- It’s actually preferable to a for-each, as it’s far more performant.
		- **The optional [select] attribute:** will process only the child elements that match.
			- We can use the "select" to specify in which order the child nodes are to be processed.
	- **The value-of element:** \<xsl:value-of select="XPATH_expression">
		- Extracts the value of an XML element and adds it to the output stream of the transformation.
		- The select attribute: contains the XPATH expression that points to the XML value.
	- **The for-each element:** \<xsl:for-each select="XPATH_expression">
		- Selects every XML element of a specified node-set
		- The select attribute: contains the XPATH expression that points to the XML value/s.
		- **The sort element:** \<xsl:sort select="XPATH_expression">
			- Sorts the iteration’s elements.
			- Place the sort element in the first line of the for-each statement.
			- The select attribute: indicates what XML element to sort on.
	- **The if element:** \<xsl:if test="XPATH_predicate_expression">
		- Puts a conditional test against the content of the XML file.
		- The select attribute: contains the expression to be evaluated.
	- **The choose element:** 	\<xsl:choose>
                              \<xsl:when test="XPATH_predicate_expression">
                              ... \</xsl:when> ...
                              \<xsl:otherwise>
                              ... </xsl:otherwise>
                              </xsl:choose>
		- It’s basically a case-switch-default statement. 
	- **The element element:** 	\<xsl:element name="XPATH_expression" [...]*>
		- Used to create an element node in the output document.
	- **The copy element:** 		\<xsl:copy [use-attribute-sets="name-list"]*>
		- Creates a copy of the current node with namespace, but not its children or attributes!

- **Attributes:**
	- To replace an attribute within a tag with the value of an XPATH query simply use {}. 
		\<xmlTag attribute="{XPATH_expression}">
	- Alternatively, under the relative xmlTag add: The attribute element:
		\<xsl:attribute name="attributeName" select="XPATH_expression">

---

- **External Links**
[W3 school Xsl reference](https://www.w3schools.com/xml/xsl_intro.asp)
- **Tools & Lab**
[Tool: Online XML - XSD formatter xsl tranformer](http://www.freeformatter.com/xsl-transformer.html)
[**Lab**: KP Xsl exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfWkpkNk1wTmNlRkE)