
# Cognos Dashboard for Live-Streaming of the Devices data in a Automobile Manufacturing Unit.

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

1. [Download the code from the github](#1-download-the-code-from-the-github)
2. [Upload the code to Cognos BI server](#2-upload-the-code-to-cognos-bi-server)
3. [Create a Dashboard to consume the Custom Widget](#3-create-a-dashboard-to-consume-the-custom-widget)
4. [Run and Analyze the Dashboard](#4-run-and-analyze-the-dashboard)


## 1. Download the code from the github

- In this repository, custom widget code is available at `./custom-widget-code`. [Dowload the `CognosCustomWidget.zip` to your machine](https://github.com/srikanthIBM/cognos-dancing-dashboard/tree/master/custom-widget-code/CognosCustomWidget.zip)


![Download_Code_Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/download_code.jpg)


## 2. Upload the code to Cognos BI server

- Launch Cognos BI server from the browser(Firefox is preferred). Use the url as per your Cognos Instance. 
Sample URL as follows: http://IP(or)localhost:9310/bi/?perspective=home
 
![LaunchCognos](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/LaunchCognos.jpg)

- Under Cognos BI web browser, go to the customization option. See below screenshot for details.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/upload_BI.jpg)

-  Under Customization, use the Extension tab and upload the `CognosCustomWidget.zip` file. See below screenshot for details.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/upload_BI1.jpg)

- You will see a successful upload message.

## 3. Create a Dashboard to consume the Custom Widget

- Open New Dashboard.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/db1.jpg)

- Select the blank template.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/db2.jpg)

- Click on the Newly created Custom Widget Icon.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/cw1.jpg)

- Drag and drop the Custom Widget to the Dashboard pane. See below screenshot for details.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/cw2.jpg)

- Adjust the dragged Custom widget to fit to the required height and width within the dashboard.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/Adjust_Size.jpg)

- After adjusting the custom widet would look like below.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/Adjust_Size1.jpg)

- Save the dashboard as 'Live Streaming of Device' under My Folder of Cognos Connection.

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images/Save_Dashboard.jpg)


## 4. Run and Analyze the Dashboard

- Run the 'Live Streaming of Device' dashboard from the saved location.
 
 



# Sample output

![Img](https://github.com/srikanthIBM/cognos-dancing-dashboard/blob/master/images//Sample_Output.png)

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

