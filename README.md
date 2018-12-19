
# Cognos Dashboard for Live-Streaming of the Devices data in Manufacturing Unit.

In this Code Pattern, we will build a Cognos add-on to consume highly volatile streaming data, a dancing dashboard. 
The real time Dashboard will be able to display mix of data (volatile and non-volatile) can be shown on a single dashboard. Volatile data is extracted from external websites and in other words we are trying to build a Cognos add-on to consume streaming(Highly volatile )data like stock ticker or data from SCADA or IOT platform broadcast data. 
The idea is to build a dancing chart that captures volatile data and incrementally updates itself.

With the latest feature of Cognos 11.x Extensions, you now have the ability to add and remove elements in the IBM Cognos Analytics user interface for a perspective. An extension is a zip file that contains spec.json and optional images and js folders.


When the reader has completed this Code Pattern, they will understand how to:

* Build Cognos Custom Widgets
* Integrate Java Script built Extension within Cognos Dashboard
* Display mix of Historical and Live Streaming IoT data in Cognos Dashboard
* Interact with widgets within the same Cognos Dashboard

## Flow

![CDB_Cognos](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/DD_Flow.jpg)

1. Develop the code(includes spec.json, js, css, Images) to build Cognos Custom Widget(Extensions)
2. Bundle the code as a zip file.
3. Upload the zipped files into Cognos using Extensions.
4. Use the custom widget into Cognos Dashboard.
 


<!--Optionally, update this section when the video is created-->
# Watch the Video

[![](http://img.youtube.com/vi/Jxi7U7VOMYg/0.jpg)](https://www.youtube.com/watch?v=Jxi7U7VOMYg)

## Pre-requisites

* Cognos server - Have on-prim or SaaS offering of Cognos with `admin access`.
   > Note: Cognos version should be over 11.0.05.
   

# Steps

## 1. Download the code from the github

- In this repository, custom widget code is available at `./custom-widget-code`. [Dowload the `CognosCustomWidget.zip` to your machine](https://github.com/srikanthIBM/cognos-dancing-dashboard/tree/master/custom-widget-code/CognosCustomWidget.zip)


![Download_Code_Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/download_code.jpg)


## 2. Upload the code to Cognos BI server.

- Launch Cognos BI server from the browser(Firefox is preferred). Use the url as per your Cognos Instance. 
Sample URL as follows: http://IP(or)localhost:9310/bi/?perspective=home
 
![LaunchCognos](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/LaunchCognos.jpg)

- Upload the file to Cognos BI server using the customization option. See below screenshot for details.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/upload_BI.jpg)

-  Under Customization, use the Extension tab and upload the `CognosCustomWidget.zip` file. See below screenshot for details.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/upload_BI1.jpg)

- Create a Dashboard to consume the Custom Widget: 




1. 

<!--Update the repo and tracking id-->
[![Deploy to IBM Cloud](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/IBM/watson-banking-chatbot.git)

1. Press the above ``Deploy to IBM Cloud`` button and then click on ``Deploy``.

<!--optional step-->
2. In Toolchains, click on Delivery Pipeline to watch while the app is deployed. Once deployed, the app can be viewed by clicking 'View app'.
![](doc/source/images/toolchain-pipeline.png)

<!--update with service names from manifest.yml-->
3. To see the app and services created and configured for this Code Pattern, use the IBM Cloud dashboard. The app is named `watson-banking-chatbot` with a unique suffix. The following services are created and easily identified by the `wbc-` prefix:
    * `wbc-conversation-service`
    * `wbc-discovery-service`
    * `wbc-natural-language-understanding-service`
    * `wbc-tone-analyzer-service`

## Run locally

> NOTE: These steps are only needed when running locally instead of using the ``Deploy to IBM Cloud`` button.

<!-- there are MANY updates necessary here, just screenshots where appropriate -->

1. [Clone the repo](#1-clone-the-repo)
2. [Create Watson services with IBM Cloud](#2-create-watson-services-with-ibm-cloud)
3. [Import the Conversation workspace](#3-import-the-conversation-workspace)
4. [Load the Discovery documents](#4-load-the-discovery-documents)
5. [Configure credentials](#5-configure-credentials)
5. [Run the application](#6-run-the-application)

### 1. Clone the repo

Clone the `watson-banking-chatbot` locally. In a terminal, run:

```
$ git clone https://github.com/IBM/watson-banking-chatbot
```

We’ll be using the file [`data/conversation/workspaces/banking.json`](data/conversation/workspaces/banking.json) and the folder
[`data/conversation/workspaces/`](data/conversation/workspaces/)

### 2. Create Watson services with IBM Cloud

Create the following services:

* [**Watson Conversation**](https://console.ng.bluemix.net/catalog/services/conversation)
* [**Watson Discovery**](https://console.ng.bluemix.net/catalog/services/discovery)
* [**Watson Tone Analyzer**](https://console.ng.bluemix.net/catalog/services/tone-analyzer)
* [**Watson Natural Language Understanding**](https://console.ng.bluemix.net/catalog/services/natural-language-understanding)

### 3. Import the Conversation workspace

Launch the **Watson Conversation** tool. Use the **import** icon button on the right

Find the local version of [`data/conversation/workspaces/banking.json`](data/conversation/workspaces/banking.json) and select
**Import**. Find the **Workspace ID** by clicking on the context menu of the new
workspace and select **View details**. Save this ID for later.

*Optionally*, to view the conversation dialog select the workspace and choose the
**Dialog** tab, here's a snippet of the dialog:

![](doc/source/images/dialog.PNG)

### 4. Load the Discovery documents

Launch the **Watson Discovery** tool. Create a **new data collection**
and give the data collection a unique name.

> Save the **environment_id** and **collection_id** for your `.env` file in the next step.

Under `Add data to this collection` use `Drag and drop your documents here or browse from computer` to seed the content with the five documents in `data/discovery/docs`.

### 5. Configure credentials

The credentials for IBM Cloud services (Conversation, Discovery, Tone Analyzer and
Natural Language Understanding), can be found in the ``Services`` menu in IBM Cloud,
by selecting the ``Service Credentials`` option for each service.

The other settings for Conversation and Discovery were collected during the
earlier setup steps (``DISCOVERY_COLLECTION_ID``, ``DISCOVERY_ENVIRONMENT_ID`` and
``WORKSPACE_ID``).

Copy the [`env.sample`](env.sample) to `.env`.

```
$ cp env.sample .env
```
Edit the `.env` file with the necessary settings.

#### `env.sample:`

```
# Replace the credentials here with your own.
# Rename this file to .env before starting the app.

# Watson conversation
CONVERSATION_USERNAME=<add_conversation_username>
CONVERSATION_PASSWORD=<add_conversation_password>
WORKSPACE_ID=<add_conversation_workspace>

# Watson Discovery
DISCOVERY_USERNAME=<add_discovery_username>
DISCOVERY_PASSWORD=<add_discovery_password>
DISCOVERY_ENVIRONMENT_ID=<add_discovery_environment>
DISCOVERY_COLLECTION_ID=<add_discovery_collection>

# Watson Natural Language Understanding
NATURAL_LANGUAGE_UNDERSTANDING_USERNAME=<add_nlu_username>
NATURAL_LANGUAGE_UNDERSTANDING_PASSWORD=<add_nlu_password>

# Watson Tone Analyzer
TONE_ANALYZER_USERNAME=<add_tone_analyzer_username>
TONE_ANALYZER_PASSWORD=<add_tone_analyzer_password>

# Run locally on a non-default port (default is 3000)
# PORT=3000

```

### 6. Run the application

1. Install [Node.js](https://nodejs.org/en/) runtime or NPM.
1. Start the app by running `npm install`, followed by `npm start`.
1. Use the chatbot at `localhost:3000`.
> Note: server host can be changed as required in server.js and `PORT` can be set in `.env`.

<!--Add a section that explains to the reader what typical output looks like, include screenshots -->

# Sample output

![](doc/source/images/sample_output.png)

<!--Optionally, include any troubleshooting tips (driver issues, etc)-->

# Troubleshooting

* Error: Environment {GUID} is still not active, retry once status is active

  > This is common during the first run. The app tries to start before the Discovery
environment is fully created. Allow a minute or two to pass. The environment should
be usable on restart. If you used `Deploy to IBM Cloud` the restart should be automatic.

* Error: Only one free environent is allowed per organization

  > To work with a free trial, a small free Discovery environment is created. If you already have
a Discovery environment, this will fail. If you are not using Discovery, check for an old
service thay you may want to delete. Otherwise use the .env DISCOVERY_ENVIRONMENT_ID to tell
the app which environment you want it to use. A collection will be created in this environment
using the default configuration.

<!-- keep this -->
## License

[Apache 2.0](LICENSE)

