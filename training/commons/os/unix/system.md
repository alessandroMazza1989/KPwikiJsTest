---
title: System Management
description: Commands, Permissions and Privileges, Environment and Shell Variables
published: true
date: 2021-02-18T11:37:15.126Z
tags: 
editor: markdown
dateCreated: 2021-02-17T16:00:26.604Z
---

# System Management

## Basic Commands

- who			→ Prints users currently logged in this machine.
- top			→ Displays real-time information on the running processes and threads.
- df			→ Reports on the space left on the file system for all mounted partitions.
	- -h			→ Human-readable: size formatted in MBs and GBs.
- du			→ Prints number of kilobytes used by each subdirectory.
 	- -s			→ Print only a summary.
 	- **Ex1:** print sizes of all files and directories in current directory → du -s *
- free			→ Displays the amount of free and used memory in the system.
	- -m			→ Space in MBs.
- uname -a		→ Prints all system info: Machine name, kernel & version, etc.
- lsb_release -a	→ Prints version info on the linux release version running.
- ip addr		→ Prints a report on the system's network interfaces.
- id user		→ Prints information on a user and their groups.
- adduser name	→ Adds a new user to the system.
	- -m			→ It also creates the user’s home directory.
	- -p password	→ Adds the password in the same step.
	- **Ex:** add user with pw in a single step: sudo useradd -m giorgio -p PASSWORD
- useradd name	→ Same as adduser.
- passwd name	→ Assign a password to the user.
- groups		→ Display groups.
	- groups usr		→ Display the user name’s group/s.
	- Groups are stored in /etc/group.
	- The wheel group gives its users administrative privileges.
- groupadd name	→ Add a group.
- usermod		→ Modify a user account.
	- -a			→ Append user to the supplementary group(s). Use only with the -G option.
	- -G group		→ Indicates we are acting on a group.
	- **Ex:** add user to a group: sudo usermod -a -G groupName giorgio.
- sudo su user	→ Switches user in the shell. Lets you become another user within that shell.
- sudo -i -u user	→ Also switches user in the shell. Lets you become another user within that shell.

## Permissions and Privileges

- **Access rights**
	- \-	→ None
 	- r	→ Read (does not include accessing directories)
 	- w	→ Write
	- x	→ Execute (includes accessing directories)
- **Files & Directories:** To read a file, you must have execution rights over its directory, and all its parents!
- **Checking permissions** (displaying permission flags): ls -l
- **Permission flags:** -rwxrw-r-- 
	-	First element 		→  	Will be d if it's a directory.
	- First triplet		→  	Owner's permissions.
	- Second triplet		→  	Group's permissions.
	- Third triplet		→  	Others' permissions.
- sudo cmd	→ Allows the execution of a command as a superuser (admin).
- chmod	 \<class>土permission file	→ Changing file mode (its permissions). 
	- Only the owner can do it. If the file doesn’t exist it will be created with the given permissions.
	- **Class notation:** User: u / Group: g / Others: o / All: a 
	- **Permission notation**
		- Normal notation: Read: r / Write: w / Execute: x
		- Octal notation: triplet of numbers for USER - GROUP - OTHERS.

| Num 	|        Description        	| Meaning 	| Binary 	|
|:---:	|:-------------------------:	|:-------:	|:------:	|
|  0  	|  No permissions at all    	|   ---   	|   000  	|
|  1  	|  Only execute             	|   --x   	|   001  	|
|  2  	|  Only write               	|   -w-   	|   010  	|
|  3  	|  Write and execute        	|   -wx   	|   011  	|
|  4  	|  Only read                	|   r--   	|   100  	|
|  5  	|  Read and execute         	|   r-x   	|   101  	|
|  6  	|  Read and write           	|   rw-   	|   110  	|
|  7  	|  Read, write, and execute 	|   rwx   	|   111  	|

-	**Ex1:** give execution permission to a single file 			→ chmod +x filename
- **Ex2:** give execution permission to the whole folder 		→ chmod -R 755 filename
	- -R 	→ recursive (all files).
	- **Numbers explained:** 	USER → 7 : rwx  / GROUP → 5 : r-x / OTHERS → 5 : r-x.
- chown \<usr>:\<grp> file → Changing ownership of file to group grp and user urs.
	- **Ex1:** change group ownership of file to sudo group 		→ chown sudo file
	- **Ex2:** change group ownership back to your user group 		→ chown :\<grp> file
	- **Ex3:** change user ownership to root user 			→ sudo chown root file
- chgrp newGroup file	→ Change group ownership
	- -R			→ Recurse through subdirectories (apply to all subdirectories).

## Environment and Shell Variables

- **Environment variables** (UPPERCASE)
	- **Common variables**
		- $SHELL 	→ Path of the shell currently running, which should be "/bin/bash".
		- $HOME 		→ Path of the home directory.
		- $PWD 		→ Path of the working directory.
		- $PATH		→ Set of paths which contain the applications referenced by commands.
		- $USER		→ User’s name.
		- $TERM		→ Info on the current terminal.
		- $SHLVL		→ Shell level. Reports on the nesting level of the current shell.
	- **Commands**
		- setenv			→ Sets an environment variable.
		- unsetenv		→ Un-sets an environment variable.
		- printenv		→ Prints all variables and their values.
		- printenv or env	→ Prints all variables and their values.
		- export name=value	→ Sets a variable so that children processes can see it. 
			- export varname	→ If the value is already set. 
- **Shell variables** (lowercase)
 	- **Common variables**
		- $cwd		→ Current working directory.
		- $home		→ History of all entered commands.
		- $path		→ The directories the shell should search to find a command.
		- $prompt	→ Text string used to prompt for interactive commands to your login shell.
		- $history	→ Number of elements in history of all entered commands.
	- **Commands**
		- set		→ Displays or sets a shell variable.
		- unset		→ Un-sets a shell variable.

**Note:** Some variables are permanently linked between shell and environment, so changing the one also changes the other (like path and PATH).

## Installing and Managing Applications

- **Ubuntu/Debian:**
	- apt / apt-get	→ Package manager.
		- sudo apt update 		→ Updates the package repository cache. (Run this first)
		- sudo apt install app	→ Installs application app.
			- Run if you encounter the error “unable to locate package package_name”
- **RedHat/Fedora:** 
	- yum			→ Package manager.
		- sudo yum update 		→ Updates the package repository cache. (Run this first)
		- sudo yum install app 	→ Installs application app.
	- dnf			→ Package manager.
		- sudo dnf install app	→ Installs application app.

## Networking Commands