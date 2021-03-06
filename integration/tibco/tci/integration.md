---
title: Integration
description: BusinessWorks Integration App
published: true
date: 2021-06-08T13:32:54.886Z
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

### Pushing an Application to the Cloud

The following section discusses the different methods of using TIBCO Business Studio for BusinessWorks to generate deployment archives for a TIBCO BusinessWorks™ App and push the app to the cloud. In fact, after creating and testing your application in TIBCO Business Studio for BusinessWorks, you can push your application to the TIBCO Cloud Integration.

There are basically two possible scenarios for deployment:

- **1.** Deployment archives, which include an EAR archive and optionally a JSON manifest, can be exported from TIBCO Business Studio for BusinessWorks.  
> This is typically done  for later deployment to the cloud using the TIBCO Cloud™ Integration web page or TIBCO Cloud Command Line Interface (CLI).
{.is-info}

- **2.** The app can be deployed to the cloud from within TIBCO Business Studio for BusinessWorks.
> This is typically done when a developer is continuously making changes and testing them in the cloud.
{.is-info}
---
###### Manual Push to the Cloud 

**1.** Open TIBCO Business Studio for BusinessWorks.
**2.** In the Project Explorer, right-click on the application to import on TCI and select **Create Enterprise Archive (EAR).** The EAR Export window appears.
**3.** Enter an EAR Location. Click **Browse** to change the location. This will create a directory that will contain the EAR archive.
**4.** Click Finish. The EAR file will be created in the named directory. The deployment archive can now be pushed manually to the cloud at the TIBCO Cloud Integration web page.

>![tciear.png](/tciear.png)

> Through this procedure the manifest.json file can be modified and enriched before the final import to the cloud.  
{.is-info}

**5.** Log in to TIBCO Cloud™ Integration [https://cloud.tibco.com/] and select the region. Then choose the target organization (or the target child organization).
**6.** Access to the  TIBCO Cloud Integration web page.
**7.** Click on the **Create/Import** button at the top right.

>![inkedtciimportbutton_li.jpg](/inkedtciimportbutton_li.jpg)

**8.** Select from the list the app type **Integrate > BusinessWorks**. The click **next**.

>![tciapptype.png](/tciapptype.png)

**9.** Drag and Drop the EAR file and the manifest ( or browse to upload). Lastly, click on the **Import App** button

###### Direct Push to the Cloud 

As mentioned before, you can also push the app to the cloud directly from TIBCO Business Studio for BusinessWorks. When an application is pushed to the cloud an archive file is generated along with a descriptive header file. Both files are sent to the TIBCO Cloud Integration platform during a push to create or update the application in the cloud.

> Before pushing an application to the cloud from TIBCO Business Studio for BusinessWorks, make sure that the API registry for the cloud to which you are pushing the application is set correctly in the Settings dialog of the API Explorer or the Cloud Applications view.
*[For more informations see the **Connecting to TIBCO Cloud** section]*
{.is-info}

**1.** Right-click the application and select **Push to Cloud**!

>![pushtocloud_thumb_0_0.png](/pushtocloud_thumb_0_0.png).

> In case an application with the same name of the pushed one has already been deployed on the cloud in the target organization, with this pushing mode an automatic replacement will take place.  
{.is-warning}

> Generally speaking ,there are other methods for pushing an application to the Cloud. Here, the most common ones have been listed. For further information refer to the official documentation linked above.
{.is-info}

### Starting, Stopping and Scaling Apps
This section deals with starting, scaling, and stopping applications deployed to TIBCO Cloud Integration and, in particular, a newly pushed application.

After pushing an app with the Web UI, it won't initially be running. On the other hand, if the application is pushed directly to the cloud  from TIBCO Business Studio for BusinessWorks, it will start automatically creating by default an instance. **[VERIFICARE]**

> TIBCO Cloud Integration App instances are fault-tolerant; TIBCO Cloud Integration checks if app instances are still running. If it detects that an app instance has failed, it will **automatically restart** a new instance. For example, if an app's desired instance count is two, and one of the instances stops running, a second instance will be automatically started.
{.is-warning}




###### Starting and Stopping Apps

**1.** On the **Apps** page, find the app whose status you want to change.Then click the app to go to the **App Details** page.

> If there were several more apps on the page, you could click a column heading to sort the list, for example, by clicking Last Modified to find the newest apps.
{.is-info}

**2.** Find the **Instances** control at the top right of the page, which  displays the number of instances currently running. The **Status** indicator next to it displays if the app is running, scaling, or stopped.

>![inkedtciappdetailspage_li.jpg](/inkedtciappdetailspage_li.jpg)
>*Instances control panel in the App Details Page*

**3.** Click **Start** to start an app, or **Stop** to stop a running app. Alternatively, You can  start or stop an app by scaling it up or down from the App Details page, as described below.

>![app-start-stop_thumb_0_0.png](/app-start-stop_thumb_0_0.png)

> If you stop and re-start an app with multiple instances running, it will have one instance running when it is restarted, and you must scale it to start more instances.
{.is-info}

###### Scaling Apps

**1.** On the **Apps** page, find the app. Then go to the **App Details** page.
**2.** Find the scaling control in the upper right. 
**3.** Hover over the number of instances. A pair of up and down arrows appears, which you can click to change the number of instances.
**4.** Click the up arrow *to add instances* to the app, then click **Scale**.

> If the app is not running, you can start it by adding one or more instances.
{.is-info}

**5.** You can also remove instances. Click the down arrow, then click **Scale**.

> To stop an app, scale its number of instances to zero.
{.is-info}

### Viewing App Endpoints

This section is about how to view the endpoint(s) of an app on TCI.

**1.** Log in to the TIBCO Cloud Integration server.
**2.** Click the** Apps** tab. Then click the app whose endpoint you want to view.
**3.** Click the **Endpoints** tab. All endpoints are shown.

>![tciendpoints.png](/tciendpoints.png)

> For *public* and *TIBCO Cloud Mesh* endpoints: [see **Changing Endpoint Visibility** section for more details]
{.is-warning}

**4.** To download a copy of the API Spec, click the shortcut menu, then click Download spec. 
**5.** To download a link to the API Spec, click the shortcut menu, then click Copy spec URL.
**6.** Click **Publish to Mashery** to publish the endpoint to Mashery.

> For *public* endpoints only:
{.is-warning}

**7.** Click the **Test** button to display the contents of the URL in Swagger in a panel within this tab.




**8.** You can click methods to expand them and use the **Try it out** button to test the endpoints.

>![tcitest.png](/tcitest.png)

**9.** To copy an app's endpoint URL to the clipboard, click the Copy URL button next to the endpoint.

> Example of Public Endpoint type: **/CloudApplicationID**/your_endpoint
>>***/jzq1w3ekvl4qpoiuqbyfxwctdqw7rt7q**/api/pi/psi/...*
>
> Where the **CloudApplicationID** (or **appId**) Is a unique alphanumeric string for each application of each organization or child organization automatically and randomly generated during the deployment of the app itself.
>
> Example of TIBCO Mesh Endpoint type: **/extercom/gsbc/CloudOrganizazionID**/public_endpoint
>>**/extercom/gsbc/02RG4GY1G4KCAPP95W3VFUYC88/tci**/jzq1w3ekvl4qpoiuqbyfxwctdqw7rt7q/api/pi/psi/etl/wrappertalend/v1/tasks/executions 
>
>Where the **CloudOrganizationID** is a unique alphanumeric string for each organization or child organization. 
{.is-warning}

### Viewing Performance Monitoring Statistics

You can monitor the performance statistics of your apps on the **Monitoring** tab of an **App details** page. This tab displays process information such as the total number of processes that have completed or failed, and performance metrics such as CPU and memory usage.

### Viewing Logs

You can view app logs for your running app to monitor its performance and debug any potential issues by clicking the **Logs** tab in the **App details** page. App logs are shown for the last five minutes by default. You can also display a different time/date range of historical logs, stream real-time logs, or download app logs.

### Configuring Apps

If you needed to change the values of properties in your app that were defined by default, you can late-bind new property values for a TIBCO BusinessWorks App. On the **App details** page, in the **Environment Controls** tab, the current values of app properties can be inspected, modified, or reset to their defaults.

> Saving the new configuration changes will restart the app with the new values. This enables you to modify properties without pushing and building a new EAR file, speeding up changes for moving from test to production, or changing credentials or other variables.
{.is-info}

### Deleting Apps

**1.** On the **Apps** page, hover over your target app. Click the trash can icon.
**2.** A confirmation dialog will appear. Click **Delete** app.

## TIBCO Cloud Mesh
In TIBCO Cloud Integration each app has an endpoint visibility option, which determines if the endpoints of the app can be accessed externally or by other domains on TIBCO Cloud.

The Apps deployed to the cloud can have endpoints visible to the public or TIBCO Cloud Mesh.

- **Public:** The endpoints are available from outside of TIBCO Cloud
- **TIBCO Cloud Mesh:** The endpoints are exposed only to applications in the TIBCO Cloud. These endpoints cannot be reached by any external system, further they can only be accessed from other clients/applications from within the TIBCO Cloud, and only to users within the same organization/subscription.

> TIBCO Cloud Mesh endpoints were formerly called *private* endpoints. This term is still used in mock apps.
{.is-info}


> By default, an app will be **Public** and unsecured.
{.is-warning}

**Useful Links:**

TIBCO Cloud Mesh Documentation:
https://account.cloud.tibco.com/cloud/docs/cloud-mesh/index.html


### Changing Endpoint Visibility

This section discusses how to change an app's endpoint visibility from public to TIBCO Cloud Mesh or vice-versa:

**1.** Log in to TIBCO Cloud Integration and click the **Apps** tab.
**2.** The Set endpoint visibility option is available from an app's shortcut menu on its **App Details** page.

>![tciendpointvisibility2.png](/tciendpointvisibility2.png)

**3.** Click **Set endpoint visibility** to change from public to TIBCO Cloud Mesh or vice-versa. You are shown a warning that this can cause a service outage for the app. Lastly, click **Update** (or **Cancel**).

> Also, there is an app visibility icon on the App Details page next to the app name which will either say Public or TIBCO Cloud Mesh. You can click this icon to toggle endpoint visibility.
{.is-info}

> For non-restful endpoints, the endpoint can't be changed to TIBCO Cloud Mesh.
{.is-warning}

### Consuming a Service Deployed in TIBCO Cloud Mesh
###### Accessing Mesh Endpoints Using TIBCO Cloud Mesh

This section discusses how to use **TIBCO Cloud Mesh** in an application in the TIBCO Cloud Integration Environment and TIBCO Business Studio client. TIBCO Cloud Mesh allows you to discover any private REST endpoint exposed within TIBCO Cloud domains, in your organization or related organizations.

To use this feature, perform the following steps:
**1.** Connect to TIBCO Cloud. For information, see **Connecting to TIBCO Cloud** section.
**2.** Open the **Cloud Applications** view. Under the **Applications** section, find the **TIBCO Cloud Mesh Services** section. Then expand the section to view the services available to you.

> If your organization has related (parent or child) organizations, the screen displays all the related organizations as folders containing the services. Applications with Private endpoints (required to display the applications) are listed in the **TIBCO Cloud Mesh Services** in the **Cloud Servers** view.
{.is-info}

>![show-files-ss1_thumb_0_0.png](/show-files-ss1_thumb_0_0.png)

**3.** Right-click the mesh service and select **Import**. 
**4.** In the **Import API** dialog box, choose whether to create a new project and import API to the new project or just import to an existing project.

>![import-apii4_thumb_0_0.png](/import-apii4_thumb_0_0.png)

**5.**  if the latter is the case, click **Browse**. Then select a folder or project and click **OK**.
**6.** In the Import API screen, do **not** click **Finish**. Instead, click **Next**. On the Change Swagger name screen, enter a logical, unique name for the Swagger file. The default pregenerated name tends to be too long and include random characters.
**7.** The TIBCO Cloud Mesh service descriptor files (including the API files) are displayed in the **Project Explorer** section.
**8.** Drag and drop the mesh service from the **Project Explorer** to the application's **Process** window and select **Create Reference** from the resulting drop-down menu.
The service icon is added to the application project window.

> All reference bindings that use TIBCO Cloud Mesh are preconfigured to use a single, special HTTP client resource, called **TIBCOCloudMeshServices**. This resource cannot be changed in the reference binding.
{.is-info}

> The **Default Host** field is automatically populated with the default value: **INTERCOM_HOST**. This value is a constant and cannot be changed.
{.is-info}

> To run the client application in Studio Debugger, ensure that in the **Advanced** tab, the **Enable TIBCO Cloud Mesh Services Consumer** check box is selected.
{.is-info}








###### Accessing Mesh Endpoints Using OAuth Access Tokens

TIBCO Cloud Mesh endpoints aren't publicly visible, but they can be accessed with an **OAuth access token**.

You can generate an OAuth token in TIBCO Cloud. Access tokens are time-limited (which can actually be a disadvantage), revocable, Bearer security tokens allowing access to specific domains. They are passed in each REST request in the authorization header by using the Bearer scheme.


>`curl -X GET "https://integration.tci-devops.tibcoapps.net/extercom/gsbc/01EV73S4BGTC596M2FB8PYRMXQ/tci/csq64ekzihqnzuomkqu7evg7emkrdlqt/book1/1?query1=david" -H "accept: application/json" -H "Authorization: Bearer CIC~Rk9xZC44-cModboJ6McMFE5D"`
>
>*For example, the above REST call using curl passes an OAuth token in an authorization header to access an endpoint*

- **Generating an OAuth access token**
Log in to TIBCO Cloud and click **OAuth Access Tokens** on the **Settings** tab in the **My Profile**  menu. To add a new token, click the **Add new token** link. Then, In the **Generate OAuth2 token** window, fill in the token name and select one or more domains for which the access token applies (Integration). Lastly, select a maximum validityand click **Generate**.

In order to consume a service deployed in TIBCO Cloud Mesh from within BW through the **Invoke REST API** activity, you can follow this method:

**1.** Similarly to how you would invoke a restful public endpoint, create HTTP Client Resource and set:
- **Default Host:**  eu-west-1.integration.cloud.tibcoapps.com
- **Default Port:** 443

**2.** In the **Input** tab of **Invoke REST API** activity, provide the **ResourcePath**.

> Example of TIBCO Mesh Endpoint type: **/extercom/gsbc/CloudOrganizationID**/public_endpoint
>>**/extercom/gsbc/02RG4GY1G4KCAPP95W3VFUYC88/tci**/jzq1w3ekvl4qpoiuqbyfxwctdqw7rt7q/api/pi/psi/etl/wrappertalend/v1/tasks/executions 
>
>Where the **CloudOrganizationID** is a unique alphanumeric string for each organization or child organization. 
{.is-warning}

**3.** Add in the **DynamicHeaders** the ***Authorization*** header valorized as **"Bearer *OAuthAccessToken*"**

>![tcimeshinvokerestapi.png](/tcimeshinvokerestapi.png)


