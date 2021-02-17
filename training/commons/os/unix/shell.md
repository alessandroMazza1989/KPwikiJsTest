---
title: Shell
description: Basic Shell Concepts, Help and Manuals, Shell Management
published: true
date: 2021-02-17T15:13:11.780Z
tags: 
editor: markdown
dateCreated: 2021-02-17T15:13:11.780Z
---

# Shell

## Basic Shell Concepts

- **Basics**
	- Standard interface appearance: username@hostname:currentpath$
	- Command structure: command <-options> \<arguments> 
		- You can use more options simultaneously with a single hyphen: -vcn...
- **Special directories**
	- /	→ Root directory.
	- .	→ Current directory.
	- ..	→ Parent directory.
	- ~	→ Home directory.
- **Whitespace in paths and filenames:** '\ '.
- **Wildcards**
	- \*	→ Matches against none or more char(s) in a file or directory name. 
					Used alone refers to any and every name in a directory.
		- **Ex:** ls name* → List all files starting with "name" and followed by anything.
	- ?	→ Matches against exactly one char(s) in a file or directory name.
		- **Ex:** ls ?name → List all files starting with exactly one char and followed by "name".
- **Program interaction channels:** stdin → command → stdout, stderr
	- These are streams which can therefore be redirected and piped.
- **Multiple arguments:** To apply commands to multiple files use a space-separated list: file1 file2…
- **Running another Bash shell (in a shell):**
	- bash		→ Starts a bash shell in the shell. The former one stays in the background.
	- exit		→ Closes the shell in the foreground.

## Help and Manuals

- help			→ Provides a list of commands that can be executed in the shell.
- man command		→ Brings up a manual of the command with its options.
- command --help	→ Displays a quick manual of the command in question.
- whatis command	→ Prints a short description of the command from the manual.
- apropos keyword	→ Searches manual pages for the keyword, which can also be a regEx.

**Notes:** Manuals are stored in /usr/bin/man and /usr/share/man.

## Shell Management

- **Termination keys:** they are usually some of the following:  q, ^C, ^D. (The ^ symbol means CTRL.)
- clear			→ Clears the shell's interface of all previously displayed content.
- alias			→ Lists available aliases of commands (default) or create one.
	- **Ex:** alias name=cmd		→ Create an alias of a command.
	- **Ex:** alias name='cmd...'	→ Create an alias of a command with embedded options (or a script!).
	- **Ex:** alias u="cd ..;" 	→ Entering n "u"s goes to the parent directory n times.
- **.profile** file → Contains aliases and environment variables
	- Root .profile: default
	- Home .profile: overrides root’s .profile (file does not exist by default)
- **Command History:** 
	- **Up Arrow Key:** Scrolls through latest entered commands.
	- history	→ Prints a numbered history of all commands. (set history=num increases size.)
	- ^R 		→ Prompt a history search of commands.
- **Copy/Pasting into shell:**  
	- **Copy:** CTRL+SHIFT+C
	- **Paste:** CTRL+SHIFT+V
- **Go to start/end of line:**	
	- **Start:** CTRL+A
	- **End:** CTRL+E