---
title: Installation
description: 
published: true
date: 2021-03-18T10:21:25.796Z
tags: 
editor: markdown
dateCreated: 2021-03-18T09:06:35.517Z
---

# Installation

As you can see in the "Overview" section, MFT needs to install the Command Center and the Internet Server on two separate machines. In some cases, however, CC, IS and PS can be installed on the same machine. This approach has both advantages and disadvantages: you don't have to configure the CMS and CMA components, but since you have everything on the same machine, some default ports can coincide. 
You can also avoid installing the CMA and CMS components if the Internet Server is in the local network and not in the DMZ. In this case, pay attention to the possibility that some doors overlap; for example it is better to assign port 49464 to the PS in the config.txt file on the PS.

## Platform Server 

The installation of the PS must be performed as root user on the machine.

Just follow the doc -> https://docs.tibco.com/pub/mftps-unix/8.0.0/doc/pdf/TIB_mftps-unix_8.0_installation.pdf?id=0

When the installation is completed remember to:

- In mftps folder execute: chmod 700 cfstart cfstop
- Edit cfstart cfstop adding on top:

		export CFROOT= set your mftps folder
		export PATH=\$PATH:\$CFROOT/bin
		export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$CFROOT/libs
    
As mftps user run "sudo cfstart" and verify with command: ps -ef | grep CyberResp | grep -v grep


## Command Center

The installation of the CC must be performed as mftcc user on the machine.

Just follow the doc -> https://docs.tibco.com/pub/mftcc/8.3.0/doc/pdf/TIB_mftcc_8.3_installation.pdf?id=0

If you need to install CMS also, install IS before.

Then follow the documentation at the "Installing Connection Manager Server" paragraph.

## Internet Server

Just follow the doc -> https://docs.tibco.com/pub/mftis/8.3.0/doc/pdf/TIB_mftis_8.3_installation.pdf?id=6

If you need to install CMA you must do it at the beginning of the IS installation.

## JMS Service

Add in the path /server/webapps/cfcc/WEB-INF/lib the files tibjms.jar and jms-2.0.jar both on CC and on IS.

Configure jms queues for writing to DB in *Management/Manage Services/JMS Service/Configure JMS* section on CC.