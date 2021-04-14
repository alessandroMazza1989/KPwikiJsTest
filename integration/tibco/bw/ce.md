---
title: bwce
description: 
published: true
date: 2021-04-14T09:53:34.389Z
tags: bwce
editor: markdown
dateCreated: 2021-04-07T15:42:58.144Z
---

# BusinessWorks Container Edition

## 1.0 Getting Started
- ### 1.1 Creating the bwce base image

Useful Links: https://docs.tibco.com/pub/bwce/2.4.4/doc/html/GUID-91EA80AA-08EF-4CB3-A6A7-E8551A441AC11.html 

Download bwce: https://drive.google.com/open?id=1QpOpVLPp8lHzQgT4UDBSPH7K9p9feqyJ

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
1. Copy the com.tibco.tpshell.sap.jco_3.0.8.002 wrapper folder with the third party SAP libraries
present in the bwce_home/palettes/sap/version_number/runtime/plugins, to the resources/
addons/jars location.

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
  
5. [3.1 *Docker installation on Centos*](/integration/tibco/bw/bwce/Utility/1)
{.links-list}
6. [3.2 *Docker basic commands*](/integration/tibco/bw/bwce/Utility/2)
{.links-list}
7. [3.3 *Networking*](/integration/tibco/bw/bwce/Utility/3)
{.links-list}

