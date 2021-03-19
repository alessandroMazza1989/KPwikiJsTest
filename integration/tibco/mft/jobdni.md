---
title: Job/DNI Pros and Cons
description: 
published: true
date: 2021-03-19T10:47:04.862Z
tags: 
editor: markdown
dateCreated: 2021-03-19T10:39:04.829Z
---

# Job/DNI Pros and Cons

1. Scheduling
	 - Job: the scheduling is precise, you can run the job at a set time within the day or week
	 - DNI: execution depends on the scan interval and the moment in which the DNI is started
2. Performance
	 - Job: one file at a time is processed and transferred, the performances are not as good as the DNI
	 - DNI: thanks to the *max concurrent* field, the DNI can be multi-threaded. The transfer happens quickly even for a large number of files 
3. Concatenation
	 - Job: in case of success or failure of a job it is possible to concatenate another one to give continuity to the flow
	 - DNI: once the execution of a transfer with DNI has been completed, you have to wait for the scan interval of the next DNI to be triggered 
4. RegEx
	 - Job: it is not possible to apply RegEx that include logic in the file path bou only in the filename
	 - DNI: RegEx can be applied to filename and path