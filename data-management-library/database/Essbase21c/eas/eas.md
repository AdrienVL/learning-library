# Essbase Administration Services (EAS Lite)

## Introduction

The Essbase web interface is the modern administration interface that supports all current platform features, a lite version of Essbase Administration Services is a limited-support option for continued management of your applications if your organization isn't ready to adopt the new interface. Once the customers are familiar with the environment they can then start working on 21c.

This option is available only for Essbase 21c independent installations of Essbase.

NOTE : EAS Lite supports only features and functionality available in 11g, and not features added in later Essbase releases.

This will only work against 21c independent installation and not on the Essbase marketplace.


Estimated Lab Time: *15 minutes*.

### Objectives

This Lab provides details on how you can optionally manage applications using Essbase Administration Services (EAS) Lite

### Prerequisites

* Essbase 21 instance with Service administrator role.


## **STEP 1:** Manage an Application Using EAS Lite

Before you can connect to an application in EAS Lite, you must set it as an EAS managed application.

To manage an application using EAS Lite:

1.	Log in to the Essbase web interface using the Essbase URL. i.e. http://ip:9000/essbase/jet.
  
   Note: Please replace ip with your instance's ip.

2.	On the Applications tab click “Import” option in the Essbase web interface and click catalog. 
   ![](./images/EAS_0.png)


3.	Select “Demo_Basic.xlsx” file from:

   All Files -> Gallery -> Applications ->Demo Samples-> Block Storage.
   ![](./images/EAS_1.png)


4.	Name the application “EAS_Demo” and name the cube “Sales” and click OK.
   ![](./images/EAS_2.png)

5.	From the Actions menu to the right of the application EAS_Demo, launch the inspector, and click Settings.

6.	From the General tab, select **Managed by Essbase Administration Services**.
   ![](./images/EAS_3.png)

7.	Click Save then Ok, and then Close.

   NOTE: Once the application is EAS managed, you can only view the outline in web interface. All the changes to be done in the application will be performed using EAS console.

## **STEP 2:** Access the EAS Lite Web Console 

1.	Open a web browser and navigate to the URL of the EAS managed server. For example,
   Copy http://ip:9100/easconsole

   Note: Please replace ip with your instance's ip.

2.	Click Launch. If the EAS Lite console doesn't launch, you may need to configure your browser with a Java Web Start (javaws) plugin that can launch .jnlp files.
   ![](./images/EAS_4.png)

   Open the downloaded file: easconsole.jnlp. 
   
3. Once the below prompt is displayed, click on Run.
   ![](./images/eas_run_prompt.png)
   

4.	Log in with the username and password of your essbase instance.
   ![](./images/EAS_5.png)

5.	Go to Enerprise View-> Essbase Servers-> http: ip:9000/essbase/agent -> Applications -> EAS_Demo
   ![](./images/EAS_6.png)

6.	Expand Application “EAS_Demo”. Double click on Sales.

7.	Right click on outline and go to Edit.
   ![](./images/EAS_7.png)


8.	You can perform all the administrative tasks in the outline like the Essbase 11g version such as creation of a cube, dimension build, data loading, creation of calculation scripts, rule file and so on. 
   ![](./images/EAS_8.png)

   **NOTE**: If you want to switch back and make the application web interface managed go to Step 1: Point 6 and uncheck the option Managed by Essbase Administration Services. You cannot manage the application by EAS again, once you uncheck this option.



## Acknowledgements
* **Authors** -Sudip Bandyopadhyay, Manager, Analytics Platform Specialist Team, NA Technology
* **Contributors** - Eshna Sachar, Jyotsana Rawat, Kowshik Nittala, Venkata Anumayam
* **Last Updated By/Date** - Jyotsana Rawat, Solution Engineer, Analytics, NA Technology, April 2021

## Need Help?
Please submit feedback or ask for help using our [LiveLabs Support Forum](https://community.oracle.com/tech/developers/categories/oracle-analytics-cloud). Please click the **Log In** button and login using your Oracle Account. Click the **Ask A Question** button to the left to start a *New Discussion* or *Ask a Question*.  Please include your workshop name and lab name.  You can also include screenshots and attach files.  Engage directly with the author of the workshop.

If you do not have an Oracle Account, click [here](https://profile.oracle.com/myprofile/account/create-account.jspx) to create one.
