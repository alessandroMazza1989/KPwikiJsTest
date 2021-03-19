---
title: Hawk
description: Application Monitoring
published: true
date: 2021-03-19T12:30:05.245Z
tags: 
editor: markdown
dateCreated: 2021-03-04T16:07:13.675Z
---

TIBCO Hawk is a sophisticated event-based tool for monitoring and managing distributed applications and systems throughout the enterprise. With Hawk, system administrators can monitor application parameters, behavior, and loading activities for all nodes in a local or wide-area network and take action when pre-defined conditions occur. In many cases, runtime failures or slowdowns can be repaired automatically within seconds of their discovery, reducing unscheduled outages and slowdowns of critical business systems

Documentation cah help, check this out!!
https://docs.tibco.com/products/tibco-hawk-6-2-1

# Installation

https://docs.tibco.com/pub/hawk/6.2.1/doc/pdf/TIB_hawk_6.2_installation.pdf?id=6

Components to install:
- TIB_rv_8.4.
- TIB_hawk_6.2.0
- TIB_hkbw6_6.6.0

RVD transport configurations:
- Set parameters in file 	TIBCO_HOME/tibco/cfgmgmt/hawk/bin/DomainTransportConfig.yml

Hawk agent configuration:
- Follow the documentation and update file /TIBCO_HOME/tibco/cfgmgmt/hawk/bin/hawkagent.cfg

Hawk console configuration:
- Follow the documentation and update file 
	TIBCO_HOME/tibco/cfgmgmt/hawk/bin/hawkconsole.cfg
  
Appspace configuration:
- After installing the HKBW6 plugin, edit the config.ini file in the appspace.

> bw.hawk.hma.enabled=true
> bw.hawk.hma.transport=tibrv
> bw.hawk.hma.rv.daemon=tcp\:"daemon"
> bw.hawk.hma.rv.service="service port"
> bw.hawk.hma.rv.network=;"network"

Restart appspace to make the changes effective: from now on, a microagent will be available for each appnode, it will be used fot monitoring.


