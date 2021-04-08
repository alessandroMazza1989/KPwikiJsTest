---
title: bwce
description: 
published: true
date: 2021-04-08T08:54:08.527Z
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
FROM debian:stretch-slim
LABEL maintainer="TIBCO Software Inc."
ADD . /
RUN chmod 755 /scripts/*.sh && apt-get update && apt-get --no-install-recommends -y install unzip ssh net-tools && apt-get clean && rm -rf /var/lib/apt/lists/*
RUN groupadd -g 2001 bwce \
&& useradd -m -d /home/bwce -r -u 2001 -g bwce bwce
USER bwce
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
ENTRYPOINT ["/scripts/start.sh"]
```
Now we need to create the base image for bwce. Within the docker folder, run the command to create an image:
```
docker build -t [image name] .
```
[building_base_image(1).png](/bwce/building_base_image(1).png)

- ### 1.2 Plugins installation 
	<br/> 
#### <span style="color:red">PSGLog</span>
Before installing the PSGLog we need to customize the logs, following these steps:
1. Create the custom-logback directory within: TIBCO_HOME/bwce/bwce-runtime-<version>/tibco.home/bwce/2.4/docker/resources/addons/
1. Add the appropriately modified logback.xml file to the custom-logback directory
1. Now you need to create a new base image that includes the changes to the logback file. From the docker folder run the docker build -t tibco / bwcetest command.
1. At runtime, use the -e option CUSTOM_LOGBACK = "true"
  
To install PSGLog in docker you need:
1. Create the PSGLog.zip file containing the lib and runtime directories, located in the path TIBCO_HOME / bw / palettes / PSGLog / 1.0.2 /
1. Move the zip file to the psglog directory
1. Open the Dockerfile and write the following statement:
COPY * .zip / resources / addons / plugins

![building_base_image(1).png](/bwce/building_base_image(1).png)
  
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
- ### 2.2 Lab 2: Comunicating between containers
- ### 2.3 Lab 3: Managing the filsystem
- ### 2.4 Lab 4: Monitoring with postgres

## 3.0 Docker utility

