---
title: Integration
description: BusinessWorks Integration App
published: true
date: 2021-05-19T13:53:10.196Z
tags: 
editor: markdown
dateCreated: 2021-05-17T07:46:56.625Z
---

# BusinessWorks Integration App

## General Concepts

TIBCO Cloud Integration is TIBCO’s integration platform as a service which is designed and built for the cloud. It supports all your traditional iPaaS use cases and is optimized for REST based and API use cases.

>![tcigeneralconcepts.png](/tcigeneralconcepts.png)

**Useful Links:**

Getting Started with TIBCO Cloud™ Integration:
https://integration.cloud.tibco.com/docs/

Getting Started with TIBCO Cloud™:
https://account.cloud.tibco.com/cloud/docs/index.html

## Getting Started
### Connecting to TIBCO Cloud

This section discusses how to connect to TIBCO Cloud in the TIBCO Cloud Integration Environment using TIBCO Business Studio client.

The API settings must be configured in order to connect to the cloud. Below is illustrated the procedure.

**1.** In the lower left section of the TIBCO Business Studio, click the white downward arrow and select **Settings**.
>![settings1_thumb_0_0.png](/settings1_thumb_0_0.png)

**2.** In the Configure API Settings window, click **New**; then in the New configuration window, enter the information requested: the API registry **Name** can be any one not already existing. Provide the **URL** [https://eu.integration.cloud.tibco.com:443] and enter your **Username** and **Password**  to authenticate (the same ones that are used to login to TIBCO cloud ). Press the **Finish** button.
>![tciapireg.png](/tciapireg.png)

> You cannot run multiple clouds at the same time, or you will get an error. In Configure API Settings, uncheck the checkbox next to each configuration you don't want to use
{.is-warning}

>If you have multiple related accounts, or parent/child accounts, you might need to select one account before you can connect to the cloud.
{.is-info}

**3.**  To select one account, click on the name of the configuration you just created (in this example, '*Cloud*') and click Edit. In the Edit window, click the Accounts tab, and select one account.

>![tciaccounts.png](/tciaccounts.png)

**4.** Once you connect to the cloud, you can view the API files in the API explorer > API tab. After connecting, you can also view the **cloud applications** and **TIBCO Cloud Mesh services** in the Cloud Applications tab.

