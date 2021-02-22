---
title: XPath
description: XML Navigation
published: true
date: 2021-02-22T13:35:32.337Z
tags: 
editor: markdown
dateCreated: 2021-02-08T09:35:36.543Z
---

# XPATH

- **Goals**
1. XPath Terminology  (Nodes, Atomic values, Items)
2. Relationships between the nodes (Parent, Children, Sibling, Ancestors, Descendants)
3. XPath Syntax 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> a. Selecting nodes 
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> b. Predicates
<span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> c. Wildcards 
4. XPath Axes concept
5. XPath operators 

- **External Links**
[W3 school Xpath reference](https://www.w3schools.com/xml/xpath_intro.asp)
- **Tools & Lab**
[Tool: Online XML - XSD formatter XPath tester](http://www.freeformatter.com/xpath-tester.html)
[**Lab**: KP Xpath exercises folder](https://drive.google.com/open?id=0BydghG4Au4HfRG5iN0ctV0VLbXM)

---

- **Used to navigate through elements and attributes in an XML document**
- **NODES:** XML documents are treated as trees of nodes. There are 7 node types: element, attribute, text, namespace, processing-instruction, comment, and document nodes.
	- **Atomic Values:** nodes with no children or parent. (ie: a text node is usually atomic)
- **Relationships between Nodes:** Parent, Child, Sibling, Ancestor, Descendant.
- **SELECTIONS:** XPath uses path expressions to select nodes in an XML document.

| SELECTORS/WILDCARDS 	|                                                                                    INFO                                                                                   	|
|:-------------------:	|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| nodename            	| Selects all nodes with the name "nodename"                                                                                                                                	|
| /                   	| Selects from the root node                                                                                                                                                	|
| //                  	| Selects nodes from the current node that match the selection no matter where they are. If nothing precedes the //, then the selection is made across the entire document. 	|
| .                   	| Selects the current node                                                                                                                                                  	|
| ..                  	| Selects the parent of the current node                                                                                                                                    	|
| @                   	| Selects attributes                                                                                                                                                        	|
| *                   	| Matches any element node (selects all children of the node)                                                                                                               	|
| @*                  	| Matches any attribute node of any kind                                                                                                                                    	|
| //*                 	| Selects all elements of the document                                                                                                                                      	|
| node()              	| Matches any tag node                                                                                                                                                      	|
| \|                  	| Multiple path selection (Logical OR, ie: selects one path AND the other if present.)                                                                                      	|

---

|           PREDICATES           	|                                                                INFO                                                                	|
|:------------------------------:	|:----------------------------------------------------------------------------------------------------------------------------------:	|
| /store/book[1]                 	| Selects the first book element that is the child of the store element.                                                             	|
| /store/book[last()]            	| Selects the last book element that is the child of the store element                                                               	|
| /store/book[last() - 1]          	| Selects the last but one book element...                                                                                           	|
| /store/book[position() < 3]      	| Selects the first two book elements that are children of the store element                                                         	|
| /store/book[count(copy) < 3]     	| Selects all books that have less than 3 copies                                                                                     	|
| /store/book/price[text()]      	| Selects the text from all the price nodes                                                                                          	|
| /store/book/[title = ’bla’]      	| Selects the book node from which has a title node “bla”                                                                            	|
| //title[@lang]                 	| Selects all the title elements that have an attribute named lang                                                                   	|
| //title[@lang = 'en']            	| Selects all the title elements that have a "lang" attribute with value "en"                                                        	|
| /store/book[price > 35.00]       	| Selects all the book elements of the store element with price element with a value greater than 35.00                              	|
| /store/book[price > 35.00]/title 	| Selects all the title elements of the book elements of the store element that have a price element with a value greater than 35.00 	|
| //title[@*]                    	| Selects all title elements which have at least one attribute of any kind                                                           	|
| //title[n][m]                  	| Of the n-th element you can select the m-th element like so.                                                                       	|

- **OPERATORS: **
	- **Classic Operators:** |, +, -, *, div, =, !=, <, <=, >, >=, or, and, mod.
	- **Comparison Operators:**
		- **Value Comparison:** Value comparison can be used only to compare exactly one item to exactly one other item.
		- **General Comparison:** While value comparison operators can compare only one thing on the 																left to one thing on the right, general comparison operators can have 															one or more items on either side of the comparison.

| Value Op. 	| General Op. 	|          Meaning         	|
|:---------:	|:-----------:	|:------------------------:	|
|     eq    	|      =      	| Equal to                 	|
|     ne    	|      !=     	| Not equal to             	|
|     gt    	|      >      	| Greater than             	|
|     ge    	|      >=     	| Greater than or equal to 	|
|     lt    	|      <      	| Less than                	|
|     le    	|      <=     	| Less than or equal to    	|

***NOTE:* General operators can flexibly compare many to many: this means that the X=Y returns true if any of the elements of X is in Y.**

- **FUNCTIONS:** (For more: https://www.w3schools.com/xml/xsl_functions.asp)

| FUNCTION              	| DESCRIPTION                                                                                                                                                                                         	|
|-----------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| choose(boolean,X,Y)   	| returns one of the specified objects based on a boolean parameter. Replaces the “if()”                                                                                                              	|
| distinct-values(arg+) 	| removes duplicates from a set of values. (Often used with count.)                                                                                                                                   	|
| concat(arg+)          	| concatenates two or more strings and returns the resulting string                                                                                                                                   	|
| string(arg)           	| converts the given argument (in parentheses) or the resulting query (at the end) to a string                                                                                                        	|
| contains(X,Y)         	| determines whether the X  string contains theY string and returns boolean true or false.                                                                                                            	|
| count()               	| counts the number of nodes in a node-set and returns an integer.                                                                                                                                    	|
| sum()                 	| returns a number that is the sum of the numeric values of each node in a given node-set.                                                                                                            	|
| avg()                 	|                                                                                                                                                                                                     	|
| max() / min()         	|                                                                                                                                                                                                     	|
| current()             	| can be used to get the context node in an XSLT instruction                                                                                                                                          	|
| last()                	| returns an integer equal to the context size from the expression evaluation context.<br>This is often used with the position() function to determine if a particular node is the last in a node-set 	|
| position()            	| returns a number equal to the context position from the expression evaluation context.                                                                                                              	|
| text()                	| selects the text from the node/s.                                                                                                                                                                   	|
| name()                	| returns a string representing the full name of the node                                                                                                                                             	|
| local-name([nodeset]) 	| returns a string representing the local name of the first node in a given node-set [OPTIONAL] ignoring the namespace prefixes!                                                                      	|

- **AXES:** An axis represents a relationship to the current node, used to locate nodes relative to that node.

| FUNCTION              	| DESCRIPTION                                                                                                                    	|
|-----------------------	|--------------------------------------------------------------------------------------------------------------------------------	|
| ancestor              	| Selects all ancestors (parent, grandparent, etc.) of the current node                                                          	|
| ancestor-of-self      	| Selects all ancestors of the current node and the current node itself                                                          	|
| attribute             	| Selects all attributes of the current node                                                                                     	|
| child                 	| Selects all children of the current node                                                                                       	|
| descendant            	| Selects all descendants of the current node                                                                                    	|
| descendant-of-self    	| Selects all descendants of the current node and the current node itself                                                        	|
| following             	| Selects everything in the document after the closing tag of the current node                                                   	|
| following-sibling     	| Selects all siblings after the current node                                                                                    	|
| namespace             	| Selects all namespace nodes of the current node                                                                                	|
| parent                	| Selects the parent of the current node                                                                                         	|
| preceding             	| all nodes before the current node, except ancestors, attribute nodes and namespace nodes                                       	|
| preceding-sibling     	| Selects all siblings before the current node                                                                                   	|
| self                  	| Selects the current node                                                                                                       	|
| name()                	| returns a string representing the full name of the node                                                                        	|
| local-name([nodeset]) 	| returns a string representing the local name of the first node in a given node-set [OPTIONAL] ignoring the namespace prefixes! 	|

- **Location Path Expression for Axes:**
	- **Absolute vs Relative Paths:** Absolute:**/step/step/...** Relative: **step/step/...**
	- **A step consists of:** an axis (defines the tree-relationship between the selected and current 														nodes), a node-test (identifies a node within an axis), zero or more 															predicates (to further refine the selected node-set).
- **Step syntax:** axisname::nodetest[predicate]

| FUNCTION               	| DESCRIPTION                                                                                   	|
|------------------------	|-----------------------------------------------------------------------------------------------	|
| child::book            	| Selects all book nodes that are children of the current node                                  	|
| attribute::lang        	| Selects the lang attribute of the current node                                                	|
| child:: *               	| Selects all element children of the current node                                              	|
| attribute:: *           	| Selects all attributes of the current node                                                    	|
| child::text()          	| Selects all text node children of the current node                                            	|
| child::node()          	| Selects all children of the current node                                                      	|
| descendant::book       	| Selects all book descendants of the current node                                              	|
| ancestor::book         	| Selects all book ancestors of the current node                                                	|
| ancestor-or-self::book 	| Selects all book ancestors of the current node - and the current as well if it is a book node 	|
| child:: */child::price  	| Selects all price grandchildren of the current node                                           	|