---
title: Process Management
description: Process Handling and Running
published: true
date: 2021-02-17T15:56:30.898Z
tags: 
editor: markdown
dateCreated: 2021-02-17T15:56:30.898Z
---

# Process Management

- ps			→ Print a snapshot of running processes.
	- -a			→ All processes except session leaders and those not associated to a shell.
	- -H			→ All active processes with their nesting structure.
	- -u			→ TODO 
	- -e			→ TODO 
	- -f			→ TODO 
	- -x			→ TODO 
	- Most used: -efa	→ TODO 
	- **STAT** (Status symbols)
		- D		→ Uninterruptible sleep
		- I		→ Idle kernel thread
		- R		→ Running or runnable
		- S		→ Interruptible sleep
		- T		→ Stopped by job control signal
		- t		→ Stopped by debugger during the tracing
		- X		→ Dead
		- Z		→ Defunct ("zombie") process, terminated but not reaped by its parent
- pgrep	name		→ Print PIDs of processes that match certain criteria. TODO 
- pstree			→ Displays the processes with their tree structure (to view subprocesses).
	- -l			→ Don’t truncate lines.
	- -p			→ Shows PID.
	- -s			→ Show parent processes.
	- pstree $$		→ Starts branch from the current process (the bash shell).
	- **Ex1:** pstree -s $$	→ Displays the whole branch (with parents) of the current process.
- top			→ Display real-time information on the running processes and threads.
- watch command	→ Execute a program periodically, showing output in fullscreen in real-time.
	- -n num	→ Set update frequency interval num in seconds (no less than 0.1).
- jobs			→ List jobs associated with the current terminal with relative job number and status.
- cmd… &		→ Run command in the background (returns shell immediately, whilst process runs). When it's over, if you press enter, it returns the \[job number] and the PID.
- ^Z			→ Suspend a running process.
- sleep num 		→ It runs a process that does nothing for num seconds. (Shell becomes unavailable.)
- bg 			→ Background the process.
- fg %jobnum		→ Foreground a process.
- time cmd		→ Returns the time taken to perform the command cmd. (user is user's CPU time.)
- kill %jobnum	→ Terminate a process given its jobnum. 
- kill <-sig> pid	→ Terminate a process given its pid with a certain signal sig (optional). 
	- -2 		→ SIGINT: similar to ^C. Abort gracefully.
	- -9		→ SIGKILL: No more CPU time! Abort immediately.
- nohup program	→ It’s a POSIX command to ignore the HUP (hangup) signal. This lets the process keep running even if the shell that started it is closed. The program’s output is appended to a nohup.out file in the current directory.
	- **Ex:** nohup program & → This will directly put the process in the background as well. 
- disown		→ TODO Pnotes 2 23-24
- Backgrounding a running foreground process
	- Suspend the process with: ^Z	: bg