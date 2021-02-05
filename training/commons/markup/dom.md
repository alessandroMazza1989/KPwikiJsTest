---
title: DOM
description: Document Object Model
published: true
date: 2021-02-05T18:21:07.565Z
tags: 
editor: markdown
dateCreated: 2021-02-05T18:21:07.565Z
---

# DOM

- **Accessing the XML DOM (using Javascript):** retrieving the text value of the first ”title” element in an XML.
	- xmlDocName.getElementsByTagName("tagName")[0]^1^.childNodes[0].nodeValue;
- **Useful:** Accessing the HTML DOM (using Javascript): 
	- xmlDocName.getElementById('elementID').innerHTML;

---
^1^ The getElementsByTagName always returns an array! So [0] must always be specified