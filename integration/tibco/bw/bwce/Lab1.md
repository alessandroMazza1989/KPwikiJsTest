---
title: Lab 1
description: 
published: true
date: 2021-04-16T08:02:16.416Z
tags: 
editor: markdown
dateCreated: 2021-04-08T13:05:36.204Z
---

# Creating a REST API
The files to test the application are available at the following link: https://drive.google.com/open?id=1ma_3FcGbgFfXZ_69OJoWmPzRkCXyoTSC

![lab1.3.png](/bwce/lab1.3.png)

![lab1.4.png](/bwce/lab1.4.png)

![lab1.5.png](/bwce/lab1.5.png)
<br/>
On Linux: 
1. Within the TIBCO_HOME create the earbwce directory, in which the .ear files of the applications and the related Dockerfiles that specify the image to be created will be inserted.
1. Inside earbwce, create the REST Service directory
1. Insert the file testRest_1.0.0.ear of the REST application in the ServizioREST directory
1. Edit del Dockerfile:
	-   run the vi Dockerfile command to create and edit the Docker file
	- 	specify the starting image, which is the base docker image created initially: FROM image_name: latest
	- specify the MAINTAINER (e.g. kp)
	- add the .ear file: ADD testRest_1.0.0.ear /
	- save the Dockerfile
![lab1.1.png](/bwce/lab1.1.png)
5. within the ServizioREST directory, create the new image that contains the application: **docker build -t bwce / serviziorest.**
![lab1.2.png](/bwce/lab1.2.png)
6. Once the new bwce / serviziorest image has been created, we can run the application. For this example, the application exposes the service on port 12000, so at run time it is necessary to specify the host and container ports to tune to. Alternatively, within Dockefile you can specify the port with the **EXPOSE** command. The command to execute is :
```
docker run -p hostPort:ContainerPort [image]
```
  So in our case it will be:
```
docker run -p 12000:12000 bwce/serviziorest
```
![lab1.6.png](/bwce/lab1.6.png)

Through Postman, I call the service with the function of **GET** at
**http: // hostIP: 12000 / resource**
![lab1.7.png](/bwce/lab1.7.png)