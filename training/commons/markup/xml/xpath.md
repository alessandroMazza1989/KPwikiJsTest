---
title: XML
description: XML Navigation
published: true
date: 2021-02-08T09:35:36.543Z
tags: 
editor: markdown
dateCreated: 2021-02-08T09:35:36.543Z
---

# XPATH

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