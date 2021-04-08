---
title: bwce
description: 
published: true
date: 2021-04-08T14:57:30.312Z
tags: bwce
editor: markdown
dateCreated: 2021-04-07T15:42:58.144Z
---

# BusinessWorks™ Container Edition

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
Useful Link: https://docs.tibco.com/pub/bwce/2.2.0/doc/html/GUID-19DDF2EF-EC3C-4A33-8E3F-30761C12C130.html
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
#### <span style="color:red">SAP</span>
Useful Links: https://docs.tibco.com/pub/bwpluginsap/8.2.0/doc/html/GUID-0CE4BF32-EADF-43FB-B692-8929604A032F.html
1. From *TIB_bwpluginsap_version_buildnumber_bwce-runtime.zip* Extract the com.tibco.tpshell.sap.jco_3.0.8.002 folder at a temporary location and delete the com.tibco.tpshell.sap.jco_3.0.8.002 folder from the runtime zip.
1. Copy the libraries into a temporary folder
1. From the temporary folder use the Docker file given below to copy these jars into the base Docker image:
```
FROM tibco/bwce:latest
COPY . /resources/addons/jars
```
NB: EMS libraries have to be present in resources/addons/jars as SAP Activities require JMS.


## 2.0 Application Development
  
1. [Lab 1 *Creating a REST API*](/integration/tibco/bw/bwce/Lab/1)
{.links-list}
2. [Lab 2 *Comunicating between applications*](/integration/tibco/bw/bwce/Lab/2)
{.links-list}
3. [Lab 3 *Managing the filsystem*](/integration/tibco/bw/bwce/Lab/3)
{.links-list}
4. [Lab 4 *Monitoring with postgres*](/integration/tibco/bw/bwce/Lab/4)
{.links-list}
5. [Lab 5 *Consul for Service*](/integration/tibco/bw/bwce/Lab/5)
{.links-list}
  
<br/>

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

Useful link: https://docs.docker.com/engine/reference/commandline/docker/
- **Docker version**
This command is used to get the currently installed version of docker
```
docker-version
```
- **Docker run**
This command is used to create a container from an image
```
docker run <image name>
```
- **Docker ps**
This command is used to list the running containers
```
docker ps
```
- **Docker exec**
This command is used to access the running container
```
docker exec -it <container id> /bin/bash
```
- **Docker stop**
This command stops a running container
```
docker stop <container id>
```
- **Docker kill**
This command kills the container by stopping its execution immediately.
```
docker kill <container id>
```
- **Docker rm**
This command is used to delete a stopped container
```
docker rm <container id>
```
- **Docker rmi**
This command is used to delete an image from local storage
```
docker rmi <image-id>
```
- **Docker build**
This command is used to build an image from a specified docker file
```
Usage: docker build <path to docker file>
```

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
Or inspect the info of a container directly
```
docker inspect [container_id]
```
In addition, it is possible to navigate inside a container
```
docker exec -it [container_id] /bin/bash
```

