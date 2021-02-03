# Create Migration Project in Oracle APEX

## Introduction

Although you can quickly build a new application within Oracle Application Express, it may seem quicker to just build an application from scratch rather than loading the source application definitions into an Oracle Application Express migration project. The value of utilizing a migration project comes from being able to view and annotate all of the business logic, generally hidden in the many Forms triggers.

Developers do not need to be an expert in Oracle Forms and need to know how to locate this business logic within Oracle Forms, as it is easily viewed within the migration project. Developers can readily cut and paste any SQL into the new component within Application Express. Also developers do not need to have Oracle Forms installed onto their computers.

The migration project is designed to ensure all of the important business logic implemented in the Oracle Forms application is migrated. However, it also helps to allocate work and track migration progress.

Estimated Lab Time: 5 minutes

### Objectives

* Create the Schema for Oracle APEX application


### Prerequisites

- Have Oracle Autonomous Database already running in OCI.
- Have Oracle APEX Workspace defined for the migration project



## **STEP 1**: **Download the Sample Scripts and Form**

1. Download the  sample forms and sample database scripts from [here](https://objectstorage.us-ashburn-1.oraclecloud.com/p/k9m-8Ft1Q5l8Bk880FkfX-hA8iGcxgjNNnyqFNLzwM-gx_T154_DkWOVH54Qjoue/n/c4u03/b/developer-library/o/create-apex-forms.zip)
to use in the lab

2. Unzip the files in your local Desktop

## **STEP 2**: **Create Schema Objects**: Run the Scripts

In order to start the conversion process, the database objects associated with your Oracle Forms application must reside in the same database as Oracle APEX.

1. From the VNC session created in previous step, Open the Oracle APEX Workspace log in page, enter **``SecretPassw0rd``** for the password, check the **Remember workspace and username** checkbox, and then click **Sign In**.
    ![](images/log-in-to-workspace.png " ")

2. Navigate to **SQL scripts** from the Oracle APEX home Page
    ![](images/scipts_upload.png " ")

3. Upload the scripts **forms_conversion_ddl.sql** and  **conversion_data_insert.sql** from your local desktop into APEX ![](images/script_upload1.png " ")

4. **Run** the script to create the schema objects for customer and orders form ![](images/scripts_run.png " ")



## **Summary**

At this point, you know how to create an APEX Migration Project and you are ready to start modernizing your forms application fast.

You may now *proceed to the next lab*.

## **Acknowledgements**

  - **Author** -  Vanitha Subramanyam, Senior Solution Architect
  - **Contributors** - Abhinav Jain, Staff Cloud Engineer, Sakthikumar Periyasamy Senior Cloud Engineer, Nayan Karumuri Staff Cloud Engineer
  - **Last Updated By/Date** - Vanitha Subramanyam, Senior Solution Architect, February 2021
## Need Help?
  Please submit feedback or ask for help using our [LiveLabs Support Forum](https://community.oracle.com/tech/developers/categories/forms-to-apex-migration-workshops). Please click the **Log In** button and login using your Oracle Account. Click the **Ask A Question** button to the left to start a *New Discussion* or *Ask a Question*.  Please include your workshop name and lab name.  You can also include screenshots and attach files.  Engage directly with the author of the workshop.

  If you do not have an Oracle Account, click [here](https://profile.oracle.com/myprofile/account/create-account.jspx) to create one.
