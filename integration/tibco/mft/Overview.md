---
title: Overview
description: 
published: true
date: 2021-03-18T09:53:39.617Z
tags: 
editor: markdown
dateCreated: 2021-03-18T09:08:37.336Z
---

# Overview

![mft_structure.png](/mft_structure.png)

TIBCO MFT is mainly composed of three elements: the Command Center, the Platform Server and the Internet Server.

## Command Center

The Command Center (CC) provides a graphical interface to manage all file transfers, both inside and outside the corporate infrastructure and therefore to all major platforms (SFTP Server, JMS, etc.).
It is in this section that users and groups are created, servers to interact with are added, transfers are configured and scheduled. The Command Center is installed in the corporate network and it is accessed from the browser.

## Platform Server

One or more Platform Servers (PS) can be installed in the corporate network to manage the file transfer activity on all the company's platforms. The Platform Server includes DNI functionality: it can search files located in a directory or subdirectory and automatically transfer or download them from one or more remote systems.

## Internet Server

The Internet Server (IS), usually located in the DMZ, is the main component of MFT through which all file transfers with external users are executed. It also exposes an Internet Server Client that offers users the possibility to upload or download files through virtual folders identified by aliases. The Internet Server can also perform the function of forwarder: by sending a file in FTP / SFTP to a virtual folder (virtual alias) on the IS, it is sent directly to the real path of the destination server.