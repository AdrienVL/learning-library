# Introduction

## About Oracle Spatial Studio

 Oracle Spatial Studio (Spatial Studio) provides no-code access to the spatial capabilities of Oracle Database. While these capabilities have historically required coding and/or use of 3rd party tools, Spatial Studio allows business users to create and share spatial analysis and interactive web maps using self-service GUIs. 

  ![img alt text](./images/spatial-studio.png)

Spatial Studio operates on spatial data in Oracle Database, meaning tables and views that include Oracle's geometry data type. This data be be pre-existing spatial data or non-spatial data which is prepared using Spatial Studio to add geometries based on attributes. The end user features of Spatial Studio can be summarized as follows:

  **Access and prepare spatial data**
  - Access spatal/non-spatial data in Oracle Database
  - Load data from common formats
  - Prepare non-spatial data by geocoding addresses or indexing lat/lon columns
  - Pre-cache large datasets

  **Analyze and visualize spatial data**
  - Drag-and-drop map visualizations
  - Data driven styling
  - Perform spatial analyses
  - Share results

Spatial Studio also provides integration features for developers and configuration options for application administrators, which are outside the scope of this intro workshop.

For more information please visit [https://oracle.com/goto/spatialstudio] (https://oracle.com/goto/spatialstudio)

Estimated Workshop Time: xx minutes

### Workshop Overview

In this workshop you will provision Spatial Studio from the OCI Cloud Marketplace and prepare a schema in Autonomous Database to be used as Spatial Studio's metadata repository.


### Prerequisites

- This workshop requires an Oracle Autonomous Database, SQL Developer Web (or other SQL client), and access to the OCI Cloud Marketplace. 
- If you already have access to these, then following this Introduction you may skip to the Lab 3. 
- Otherwise you should proceed to Lab 1.
- No previous experience with Oracle Spatial is required.


## Acknowledgements

* **Author** - David Lapp, Database Product Management, Oracle
* **Last Updated By/Date** - 


## Need Help?
Please submit feedback or ask for help using our [LiveLabs Support Forum](https://community.oracle.com/tech/developers/categories/oracle-spatial). Please click the **Log In** button and login using your Oracle Account. Click the **Ask A Question** button to the left to start a *New Discussion* or *Ask a Question*.  Please include your workshop name and lab name.  You can also include screenshots and attach files.  Engage directly with the author of the workshop.

If you do not have an Oracle Account, click [here](https://profile.oracle.com/myprofile/account/create-account.jspx) to create one. 
