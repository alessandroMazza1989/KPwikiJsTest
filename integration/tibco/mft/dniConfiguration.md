---
title: DNI Configuration
description: 
published: true
date: 2021-03-19T10:32:40.374Z
tags: 
editor: markdown
dateCreated: 2021-03-19T10:30:23.116Z
---

# DNI Configuration

Through the DNI functionality, a Platform Server is able to search files located in a directory or subdirectory and automatically transfer or download them from one or more remote systems. When a DNI transfer is created, the Platform Server scans a local or remote folder at user-defined time intervals, keeping track of the list of files in it. Any new file will be transferred. Once the transfer is complete, DNI can delete the original file or move it to a new directory.

There are two types of configurable DNI: DNI send and DNI receive.

- DNI send: it reads in the predefined local folders and in the presence of added or modified files sends these ones to the remote system
- DNI receive: through the Platform Server instance of the Internet Server it extracts the list of the files in the remote folder and, as in the previous case, downloads the files to the local Platform Server


---
To enable the Platform Server on the Internet Server, go to *Administration/System Configuration/Platform Server/Configure Platform Server* (default port: 46464).
To install DNI function, go to the *<mftps_home>/dni* path and extract the dni.tar file with the command
tar -xvf dni.tar

Backup the DNIConfig.cfg file and modify the following parameters:

- ListenIPPort: 		(default 47777)
- AcceptIPAddress:	Ip Address of the CC

Run the perl command 
- 		DNIDaemon.pl c: DNIConfig.cfg encrypt 
and enter UserID and password where required. Then run the perl command 
-		DNIDaemon.pl c: DNIConfig.cfg
In the Platform Server settings, update the section shown in the following image.

