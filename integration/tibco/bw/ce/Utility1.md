---
title: 3.1
description: 
published: true
date: 2021-04-16T08:17:00.477Z
tags: 
editor: markdown
dateCreated: 2021-04-09T07:16:42.399Z
---

# Docker installation on Centos
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