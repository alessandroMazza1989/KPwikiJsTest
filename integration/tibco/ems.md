---
title: EMS
description: Enterprise Message Service
published: true
date: 2021-03-04T10:17:22.460Z
tags: 
editor: markdown
dateCreated: 2021-02-22T14:28:51.846Z
---

# EMS

## Setup (for RedHat)

- Download setup file: TIB_ems-ce_8.5.0_linux_x86_64.zip
- Unzip it.
	- unzip TIB_ems-ce_8.5.0_linux_x86_64.zip
- Install it: the software will be installed for the root user at the path /opt/tibco
	- sudo yum install -y rpm/*.rpm

### Setup “tibco” OS User (optional, but recommended)

- Create a user named “tibco” belonging to the “tibco_group”. (Option -m to add home folder too.)
	- sudo adduser -m tibco
	- sudo passwd tibco PASSWORD
- Assign administrative privileges (assign group “wheel”) 
	- sudo usermod -a -G wheel tibco
- Change ownership of tibco folder and subfolders to tibco user and tibco_group group.
	- sudo chown -R tibco /opt/tibco
	- sudo chgrp -R tibco_group /opt/tibco
- Create the datastore folder.
	- mkdir /home/tibco/datastore
- Open the following file with an editor: /opt/tibco/ems/8.5/samples/config/tibemsd.conf
- Where it says "store" substitute the path datastore with /home/tibco/datastore

## Starting the Server

- Access OS as tibco user.
- Start the server (Method 1):
	- Go to directory: /opt/tibco/ems/8.5/bin.
	- Start the server:
		- ./tibemsd -config /opt/tibco/ems/8.5/samples/config/tibemsd.conf
- Start the server (Method 2):
	- /opt/tibco/ems/8.5/bin/tibemsd -config /opt/tibco/ems/8.5/samples/config/tibemsd.conf

## Starting an Admin Client and Connecting

- Go to directory: /opt/tibco/ems/8.5/bin.
- Start an (admin) client.
	- ./tibemsadmin
- Connect to the instance (default port is 7222). Two alternatives:
	- connect  				← Connects directly to localhost:7222 
	- connect tcp://host:port 	← Connects to the given host and port.
- Enter username and password. 
	- Default admin is “admin” with no password.

## EMS Console Commands

- help 			→ Displays the list of available commands
	- Output:
> add
addprop
autocommit
commit
compact
connect
create
delete
disconnect
echo
exit
grant
help
info
jaci
purge
remove
removeprop
resume
revoke
rotatelog
set
setprop
show
showacl
shutdown
suspend
time
timeout
transaction
updatecrl
whoami

- help cmd		→ Shows info on the command cmd.
- show arg 		→ Shows information on a certain arg. 
- showacl name		→ Shows permission of a certain arg which can be a group or a user.

## Notes: Wildcards, Datastores, etc

- Dynamic Queues: queueBranch.queueName.> VS queueBranch.queueName.*
	- \> → Symbolizes all subqueues of queueName, and their subqueues recursively.
	- * → Symbolizes all subqueues of queueName without any sub-subqueues.
- Datastores: 
	- One can set up multiple datastores, often used for backup or for safety.
	- Datastores, like in this document’s case, can be set up on the file system, however they can often be configured on a database.

## Example 

- Connect to the instance.
	- connect
	- Use username “admin” and no password.
- Create user "user1" with password "user1".
	- create user user1 password=user1
- Create group "developers".
	- create group developers
- Add user "user1" to the group "developers".
	- add member developers user1
- Create 2 queues "test.trasporto" and "test.libro".
	- create queue test.trasporto
	- create queue test.libro
- Give group "developers" create, view, browse, modify, delete, purge, receive, and send permissions on the dynamic queue "test.>".
	- Either use this sequence of commands:
		- grant queue test.> group=developers create
		- grant queue test.> group=developers view
		- grant queue test.> group=developers browse
		- grant queue test.> group=developers modify
		- grant queue test.> group=developers delete
		- grant queue test.> group=developers purge
		- grant queue test.> group=developers receive
		- grant queue test.> group=developers send
- Or use a single command with comma-separated permissions:
	- grant queue test.> group=developers create, view, browse, modify, delete, purge, receive, send
- Or use a single command with “all” if you want to grant all permissions:
	- grant queue test.> group=developers all

## Uninstall

- https://docs.tibco.com/pub/ems/8.5.1/doc/html/GUID-0790B99F-7E21-4510-8C6E-A8A1A0E06E39.html

## GEMS - The Graphical Administration Tool for TIBCO EMS

### Setting up and Running the Gems Tool (on RedHat)

- Make sure you have java installed, or install it now.
	- sudo yum install java-1.8.0-openjdk-devel
- Download
	- https://community.tibco.com/modules/graphical-administration-tool-tibco-ems 
- Unzip
- Edit rungems.sh script: set TIBEMS_ROOT to the current path of the version of ems
	- TIBEMS_ROOT=/opt/tibco/ems/8.5
- Configure servers
	- Make sure there are only the servers you need. 
	- Each server is a \<ConnectionNode> element.
	- To try this out only one \<ConnectionNode> is necessary.
	- Edit \<ConnectionNode> element to reach the current EMS server.
		- Set alias att\ribute to an arbitrary name.
		- Set url attribute to the server’s url; in this case: “tcp://localhost:7222”.
		- Set user attribute to the desired username; in this case: “admin”.
		- Set password attribute to the user’s password; in this case none: “”.
- Run tool by running the rungems.sh script.
	- ./rungems.sh

### Using the Gems Tool (WIP)

![ems_gems.png](/ems_gems.png)

- Top Menu - Queues
	- Browse Queue
		- Selector: uses the SQL’s “where” syntax to filter by the properties (columns) of messages.
	- Send Text Message
		- Top Menu - Add Custom Property
- TODO: Formalize creation of many users with different permissions.