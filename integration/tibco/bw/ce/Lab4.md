---
title: Lab 4
description: 
published: true
date: 2021-04-16T08:06:53.706Z
tags: 
editor: markdown
dateCreated: 2021-04-08T13:09:22.696Z
---

# Monitoring with postgres
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