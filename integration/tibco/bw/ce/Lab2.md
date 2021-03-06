---
title: Lab 2
description: 
published: true
date: 2021-04-16T08:05:51.106Z
tags: 
editor: markdown
dateCreated: 2021-04-08T13:07:19.627Z
---

# Comunicating between applications
The files to test the application are available at the following link: https://drive.google.com/open?id=1fgXdo7FDwWBpfAo2D3W2hpj0Rsa6PGDx

In this Lab we are going to create an application that calls the REST API created in Lab 1.

![lab2.1.png](/bwce/lab2.1.png)

![lab2.2.png](/bwce/lab2.2.png)

On Linux:
1. 	create a new directory  chiamaServizioRest
1. 	insert the appropriately modified Dockerfile and the application .ear file inside it
  
Build the calling service image inside the directory callServizioRest: **docker build -t bwce / callest service.**

  Then fisrt run the image that exposes the REST service: 
```
docker run -p 12000:12000 bwce/serviziorest
```
Afterwards run the calling image:
```
docker run bwce/chiamaserviziorest
```
![lab2.3.png](/bwce/lab2.3.png)