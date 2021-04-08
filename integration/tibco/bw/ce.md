---
title: bwce
description: 
published: true
date: 2021-04-08T12:51:02.236Z
tags: bwce
editor: markdown
dateCreated: 2021-04-07T15:42:58.144Z
---

# BWCE

## 1.0 Getting Started
- ### 1.1 Creating the bwce base image

Useful Links: https://docs.tibco.com/pub/bwce/2.4.4/doc/html/GUID-91EA80AA-08EF-4CB3-A6A7-E8551A441AC11.html 
\
Download bwce: https://drive.google.com/open?id=1QpOpVLPp8lHzQgT4UDBSPH7K9p9feqyJ
\
On Linux, create the bwce folder inside TIBCO_HOME and move the bwce-runtime- 	2.4.4.zip installation file to it:
```
	mkdir /bwce
	mv bwce-runtime-2.4.4.zip /bwce/.
	unzip bwce-runtime-2.4.4.zip -d bwce-runtime-2.4.4
```
Move the bwce-runtime-2.4.4.zip file to the following path:
```
mv bwce-runtime-2.4.4.zip /bwce/<version_number>/docker/resources/bwce-runtime
```
Open the Dockerfile and replace its contents with:
```
FROM centos:7
LABEL maintainer="TIBCO Software Inc."
ADD . /
RUN chmod 755 /scripts/*.sh && yum -y update && yum -y install unzip ssh net-tools
ENTRYPOINT ["/scripts/start.sh"]
```
Now we need to create the base image for bwce. Within the docker folder, run the command to create an image:
```
docker build -t [image name] .
```
![building_base_image(1).png](/bwce/building_base_image(1).png)

- ### 1.2 Plugins installation 
	<br/> 
#### <span style="color:red">PSGLog</span>
Before installing the PSGLog we need to customize the logs, following these steps:
1. Create the custom-logback directory within: **TIBCO_HOME/bwce/bwce-runtime-<version>/tibco.home/bwce/2.4/docker/resources/addons/**
1. Add the appropriately modified logback.xml file to the custom-logback directory
1. Now you need to create a new base image that includes the changes to the logback file. From the docker folder run the docker build -t tibco / bwcetest command.
1. At runtime, use the -e option CUSTOM_LOGBACK = "true"
  
To install PSGLog in docker you need:
1. Create the PSGLog.zip file containing the lib and runtime directories, located in the path **TIBCO_HOME/bw/palettes/PSGLog/1.0.2/**
1. Move the zip file to the psglog directory
1. Open the Dockerfile and write the following statement:
**COPY * .zip /resources/addons/plugins**

![psglog_dockerfile.png](/bwce/psglog_dockerfile.png)
  
 Finally, create the image with the following command
```
docker build -t tibco/bwce .
```

#### <span style="color:red">EMS</span>
To add the TIBCO Enterprise Message Service™ client libraries to the TIBCO BusinessWorks™ Container Edition runtime environment:
1. Copy the TIBCO Enterprise Message Service™ OSGi client libraries from <EMS-HOME>/components/1.0/plugins into a temporary folder. ![emslibraries.png](/bwce/emslibraries.png)
1. From the temporary folder use the Docker file given below to copy these jars into the base Docker image:
```
FROM tibco/bwce:latest
COPY . /resources/addons/jars
```
3.   From the temporary folder, build the Docker image:
```
docker build -t tibco/bwce .
```

## 2.0 Application Development
- ### 2.1 Lab 1: Creating a REST API 
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

- ### 2.2 Lab 2: Comunicating between applications

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

- ### 2.3 Lab 3: Managing the filsystem
The files to test the application are available at the following link: https://drive.google.com/open?id=185i9v15uf4U5BkmzWaLdtxp-Bl73IyW0

Useful Links: https://docs.docker.com/storage/volumes/

At the filesystem level, each container is completely isolated from the underlying system and from that of all other containers. For this reason, when you want to access a file on the host from the container, you need to use the volume drivers.
  
![lab3.1.png](/bwce/lab3.1.png)

Let's create a Studio application that reads the file.txt  on the host and writes its contents to the fileModified.txt. Finally, every time the fileModified.txt is written, we notify through a filePoller.

![lab3.2.png](/bwce/lab3.2.png)

![lab3.3.png](/bwce/lab3.3.png)

![lab3.4.png](/bwce/lab3.4.png)

On Linux: 
1. 	we create the readFile directory and insert the .ear file and the Dockerfile
1. create the image: **docker build -t bwce / readfile.**
1. create in the root a directory called condivisaDocker, which will contain the file.txt to read

To mount a specific directory located on your host as a Docker volume inside the container, add the following argument to the docker run command:
```
-v [host directory]:[container directory]
```
The host_directory and continer_directory are the absolute paths.  According to the example, the run command will be: 

```
docker run --name bwce-filesystem -v /condivisaDocker:/hostVolume bwce/readfile
```

Once run, we inspect the container to make sure the container directory has been created correctly. To do so we need to launch the following command: 
```
docker exec -it bwce-filesystem /bin/bash
```

![lab3.5.png](/bwce/lab3.5.png)

Accessing the hostVolume directory we will see the file.txt and fileModified.txt

![lab3.6.png](/bwce/lab3.6.png)

- ### 2.4 Lab 4: Monitoring with postgres

Useful Link: https://hackernoon.com/dont-install-postgres-docker-pull-postgres-bee20e200198

Doc pag. 15: https://docs.tibco.com/pub/bwce/2.4.1/doc/pdf/TIB_bwce_2.4.1_application_monitoring_and_troubleshooting.pdf?_ga=2.228605596.101666866.1561367010-1826608602.1558077978

In this Lab we are going to install postgres as a container and then monitor bwce applications.

Docker provides an image containing the DB functionalities.
Pull Postgres Image:

```
docker pull postgres
```
Create a directory to use as the localhost mount point for the Postgres data files
```
mkdir -p $HOME/docker/volumes/postgres
```
Run postgres container
```
docker run --rm --name pg-docker -e POSTGRES_PASSWORD=postgres -d -p 5432:5432 -v $HOME/docker/volumes/postgres:/var/lib/postgresql/data  postgres
```
Build the BWCE Application Monitor

1. Download bwce_mon.zip TIBCO BusinessWorks Container Edition monitoring zip file: http://edelivery.tibco.com.
1. Inside the TIBCO_HOME create the dockerMonitor directory and run the unzip
1. build the image:
```
docker build -t bwce/monitoring:latest .
```
We can monitor any application contained in an image:
```
docker run -d -p AppPort:AppPort -e BW_APP_MONITORING_CONFIG='{"url":"http://IPdockerMonitor:portMonitor"}'  [image]
```
## 3.0 Docker utility
- ### 3.1 Docker installation on Centos
Run the following command:
```
  sudo yum install docker
```
Once Docker is installed you need to start it with the command:
```
 systemctl start docker
```
To make sure Docker has been started correctly, you need to check its status
```
systemctl status docker
```
To activate Docker
```
  systemctl enable docker
```
To turn off Docker

```
 systemctl stop docker
```
List of docker commands

```
docker --help
```
- ### 3.2 Docker basic commands

- ### 3.3 Networking
Useful Links: https://docs.docker.com/engine/tutorials/networkingcontainers/

Even at the networking level, containers are in some ways isolated.

![utility-1.png](/bwce/utility-1.png)

Docker includes support for networking containers through the use of network drivers. By default, Docker provides two network drivers for you, the bridge and the overlay drivers. You can also write a network driver plugin so that you can create your own drivers but that is an advanced task.

Each Docker Engine installation automatically includes three default networks:

![utility-2.png](/bwce/utility-2.png)

The network called bridge is a special network. Unless a user-defined bridge is specified, Docker always launches containers on this network.

It is possible to inspect the network to obtain the IP address of the containers that are part of it, through the command:
```
docker network inspect [nome_network]
```

