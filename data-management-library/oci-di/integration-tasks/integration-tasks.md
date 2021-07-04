# Create a Data Flow, Data Integration task and Data Loader Task

## Introduction

This lab will walk you through the steps to create **two Data Flows**, **Integration tasks**, a **Data Loader task** and a **SQL task** in OCI Data Integration.

*Estimated Lab Time*: 1 hour

## Objectives
In this lab, you will:
* Create an OCI Data Integration project
* Create two Data Flows
* Create an Integration tasks
* Create a Data Loader task
* Create a SQL task

## Prerequisites
* Free Tier/ Paid Oracle Cloud Account
* All previous labs have been successfully completed

## **STEP 1:** Create an OCI Data Integration project

In Oracle Cloud Infrastructure Data Integration, a **project** is the container for design-time resources, such as tasks or data flows and pipelines.

1. In the Oracle Cloud Infrastructure Console navigation menu, navigate to **Analytics & AI**. Under Big Data, click **Data Integration**.
![](./images/menu_di.png " ")

2. From the Workspaces page, make sure that you are in the compartment for data integration (`DI-compartment`). Click on your **Workspace** (`DI-workspace`).
![](./images/workspaces-click.png " ")

3. On your workspace home page, click **Open tab** (plus icon) in the tab bar and then select **Projects**.
![](./images/click-projects.png " ")

4. On the Projects page, click **Create Project**.
![](./images/create-project.png " ")

5. On the Create Project page, enter `DI_Workshop` for **Name** and an optional **Description**, and then click **Save**.
![](./images/create-project-page.png " ")

6. You are now in the **Project Details** page for `DI_Workshop` project.
![](./images/di-workshop-project.png " ")

## **STEP 2:** Create a Data Flow - 1
A **data flow** is a logical diagram representing the flow of data from source data assets, such as a database or flat file, to target data assets, such as a data lake or data warehouse.
The flow of data from source to target can undergo a series of transformations to aggregate, cleanse, and shape the data. Data engineers and ETL developers can then analyze or gather insights and use that data to make impactful business decisions.

You will create a data flow to ingest data from **two source files**, containing customers (`CUSTOMERS.json`) and orders (`REVENUE.csv`) information.

1. From the **Project Details** page for `DI_Workshop` project, click on **Data Flows** from the submenu.
![](./images/click-data-flows.png " ")

2. Click **Create Data Flow**.
![](./images/click-create-df.png " ")

3. The data flow designer opens in a new tab. In the Properties panel, for **Name**, enter `Load Customers and Revenue Data`, and click **Save**.
![](./images/df-new.png " ")

4. You will add your **Source operator**. You add source operators to identify the data entities to use for the data flow. From the Operators panel on the left, **drag and drop a Source operator** onto the canvas.
![](./images/source-op.png " ")

5. On the canvas, select **SOURCE_1 operator**. The Properties panel now displays the details for this operator.

In the **Details** tab, click Select next to each of the following options to make your selections:
  - For **Data Asset**, select `Object_Storage`
  - For **Connection**, select `Default Connection`
  - For **Schema**, select your **compartment** and then your **bucket**. For the purposes of this tutorial, Object Storage serves as the source data asset, this is why you select your bucket here.
![](./images/comp-bucket.png " ")
  - For **Data Entity**, click on **Browse by name**. Select `CUSTOMERS.json` and then choose **JSON** for the file type.
![](./images/select-file.png " ")
![](./images/select-entity.png " ")

In the end, your details for the source operator should look like this:
![](./images/source-operator-details.png " ")

6. When you complete your selections for **SOURCE\_1**, the operator name becomes **CUSTOMERS\_JSON**, reflecting your data entity selection. In the Identifier field, rename the source operator to **CUSTOMERS**.
![](./images/customers.png " ")

7. You will now drag and drop onto the data flow canvas another **source operator**.
![](./images/new-source.png " ")

8.  On the canvas, select the new source operator. You will now fill in the details for this new source, in **Properties** panel:
  - For **Data Asset**, select `Object_Storage`
  - For **Connection**, select `Default Connection`
  - For **Schema**, select your **compartment** and then your **bucket**. For the purposes of this tutorial, Object Storage serves as the source data asset, this is why you select your bucket here.
  - For **Data Entity**, click on **Browse by name**. Select `REVENUE.csv` and then choose **CSV**  for the file type. Accept the default values for the remaining items.
![](./images/revenue-csv.png " ")

In the end, your details for this new source operator should look like this:
![](./images/csv-source.png " ")

9. When you complete your selections for **SOURCE\_2**, the operator name becomes **REVENUE\_CSV**, reflecting your data entity selection. In the Identifier field, rename the source operator to **REVENUE**.
![](./images/revenue.png " ")

10. While you still have the **REVENUE** operator selected, click on **Attributes** tab in Properties panel.
In the Attributes tab, you can view the data entity's attributes and apply **exclude** or **rename** rules to the attributes from their respective **actions icon** (three dots). You can also use the **filter** icon on the Name or Type column to apply one or more filters on the attributes to be excluded.
![](./images/prop-attributes.png " ")

11. While you still have the **REVENUE** operator selected, click on **Data** tab in Properties panel. In the Data tab, you can view a sampling of data from the source data entity. Scroll to the right and click on field REVENUE_CSV.CURRENCY to view the **data profile**.
![](./images/currency-profile.png " ")

12. In the **Validation tab**, you can check for warnings or errors with the configuration of the source operators. The message "No items found" after clicking on the Validate button tells us that there are no warnings or errors with the operator.
![](./images/validate-revenue.png " ")

13. You will now **filter your source data**. The **Filter operator** produces a subset of data from an upstream operator based on a condition. From the Operators panel, drag and drop a Filter operator onto the canvas.
![](./images/canvas-filter.png " ")

14. Connect **REVENUE** source operator to **FILTER_1** operator:
  - Place your cursor on REVENUE.
  - Click the connector circle at the side of REVENUE.
![](./images/revenue-operator.png " ")

  - Drag and drop the connector to FILTER_1.

![](./images/connect-revenue-filter.png " ")


15. Click on **FILTER_1** on the Data Flow Canvas.
![](./images/click-filter.png " ")

16. In the Properties panel of FILTER_1, click **Create** for **Filter Condition**.
![](./images/click-create-filter.png " ")

17. You will now add your **filter condition**:
  - In the Create Filter Condition panel, enter **STA** in the Incoming attributes search field
  - Double-click or drag and drop **ORDER_STATUS** to add it to the filter condition editor
![](./images/filter-cond.png " ")
  - In the condition editor, enter `='1-Booked'`, so your condition looks like the following:

`FILTER_1.REVENUE_CSV.ORDER_STATUS='1-Booked'`
![](./images/filter-condition.png " ")
*Note: To avoid issues with the quotes, do not copy and paste.*

  - Click **Create**.

![](./images/create-button.png " ")


18. The details for **FILTER_1 operator** should now look like this:
![](./images/filter-details.png " ")

19. From the Operators panel, drag and drop a new **Filter operator** onto the canvas after CUSTOMERS. **Connect CUSTOMERS to FILTER_2**.
![](./images/new-filter.png " ")

20. In the Properties panel of FILTER_2, click **Create** for **Filter Condition**.
![](./images/new-filter-cond.png " ")

21. You will now add your **filter condition** for **FILTER_2**:
  - In the Create Filter Condition panel, enter **COU** in the Incoming attributes search field
  - Double-click **COUNTRY_CODE** to add it to the Filter condition editor
  - Enter `='US'`, so your condition looks like the following: `FILTER_2.CUSTOMERS_JSON.COUNTRY_CODE='US'`
  - Click **Create**.

![](./images/new-filter-create.png " ")


22. The details for **FILTER_2 operator** should now look like this:
![](./images/filter-new-details.png " ")

23. You will now work on the **Data Transformation** part of your Data Flow. In the **Properties panel for FILTER_2**, click the **Data** tab.
All data rows and attributes are displayed. You can use the vertical scrollbar to scroll the rows, and the horizontal scrollbar to scroll the attributes.
![](./images/data-tab.png " ")

24. In the **Filter by pattern** search field, enter `STATE*`.
The number of attributes in the table are filtered. Only those attributes that match the pattern are displayed.
![](./images/filter-state.png " ")

25. Click the **transformations icon** (three dots) for `FILTER_2.CUSTOMERS_JSON.STATE_PROVINCE`, and then select **Change Case**.
![](./images/change-case.png " ")

26. In the **Change Case** dialog:
  - From the **Type** drop-down, select **UPPER**
  - Do **not** select the check box Keep Source Attributes
  - Leave the **Name** as-is
  - Click **Apply**.

![](./images/change-case-apply.png " ")


27. An **Expression operator** is added to the data flow. In the Properties panel, the Details tab is now in focus, showing the expression details. You can see the generated expression, `UPPER(EXPRESSION_1.CUSTOMERS_JSON.STATE_PROVINCE)`, in the Expressions table.
![](./images/expression-operator.png " ")

28. With the new **EXPRESSION\_1** operator selected in the data flow, in the Properties panel, change the name in Identifier to **CHANGE\_CASE**.
![](./images/expression-name.png " ")

29. Click the **Data** tab, and then use the horizontal scrollbar to scroll to the end. **EXPRESSION\_1.STATE\_PROVINCE** is added to the end of the dataset. You can preview the transformed data for EXPRESSION\_1.STATE\_PROVINCE in the Data tab.
![](./images/state-province.png " ")

30. From the Operators panel, drag and drop a **new Expression** operator onto the canvas after **CHANGE_CASE** operator. **Connect CHANGE\_CASE to the new Expression**.
![](./images/new-expression.png " ")

31. With **EXPRESSION\_2** selected, in the Properties panel, change the name in Identifier to **CONCAT\_FULL\_NAME** and then click **Add Expression** button in the Expressions table.
![](./images/add-expression.png " ")

32. In the **Add Expression** panel:
  - Rename the expression to `FULLNAME` in the **Identifier** field
  - Keep **Data Type** as `VARCHAR`
  - Set **Length** to `200`
  - Under Expression Builder, switch from the Incoming list to the **Functions list**
  - In the **filter by name search field**, enter `CON`. Then locate `CONCAT` under String. You can either search for CONCAT in the functions list yourself, or enter CON to use the auto-complete functionality
  - Enter
  `CONCAT(CONCAT(EXPRESSION_1.CUSTOMERS_JSON.FIRST_NAME, ' '),EXPRESSION_1.CUSTOMERS_JSON.LAST_NAME)` in the **expression box**.
You can also highlight a function's placeholders and then double-click or drag and drop attributes from the Incoming list to create an expression.
  - Click **Add**.

![](./images/expression-conditions.png " ")


33. The new expression is now listed in the **Expression operator**. You can add as many expressions as you want.
![](./images/final-expression.png " ")

34. After you apply filters and transformations, you can join the source data entities using a unique customer identifier, and then load the data into a target data entity.
To join the data from expression **CONCAT\_FULL\_NAME** with the data from **FILTER\_1**, drag and drop a **Join operator** from the Operators panel onto the canvas next to CONCAT\_FULL\_NAME and FILTER\_1. Connect CONCAT\_FULL\_NAME to JOIN\_1 and then connect FILTER\_1 to JOIN\_1.
![](./images/add-join.png " ")

35. With **JOIN\_1** selected, in the Details tab of the Properties panel, click **Create** next to **Join Condition**.
![](./images/create-join-cond.png " ")

36. In the **Create Join Condition panel**:
  - Enter `CUST` in the filter by name search field
  - You want to join the entities using CUST\_ID and CUST\_KEY. In the editor, enter `JOIN_1_1.CUSTOMERS_JSON.CUST_ID=JOIN_1_2.REVENUE_CSV.CUST_KEY`
  - Click **Create**.

![](./images/join-cond.png " ")


37. Your **Join operator properties** should now look like this:
![](./images/join-prop.png " ")

38. From the Operators panel, drag and drop a **Target operator** onto the canvas. Connect JOIN\_1 to TARGET\_1.
![](./images/target-op.png " ")

39. With **TARGET_1** selected on the canvas, in the **Details** tab of the Properties panel complete the fields accordingly:
  - Leave the default value for **Integration Strategy** as **Insert**
  - For **Data Asset**, select `Data_Warehouse`
  - For **Connection**, select `Beta Connection`
  - For **Schema**, select `BETA`
  - For **Data Entity**, select `CUSTOMERS_TARGET`
  - For **Staging Location**, select the **Object Storage data asset**, its **default connection** and your **compartment**. Then for **Schema**, select the **Object Storage bucket** that you created before importing the sample data (in Lab 0). Click **Select**.

![](./images/staging-location.png " ")


40. The properties details for **CUSTOMERS_TARGET operator** should now look like this:
![](./images/target-operator-properties.png " ")

41. To review the Attributes mapping, click the **Map tab**. By default, all attributes are **mapped by name**. For example, CUST\_ID from JOIN\_1 maps to CUST\_ID in the target data entity.
![](./images/mappings.png " ")

42. To manually map attributes that are not yet mapped, click the **All** drop-down in the Target attributes table, and then select **Attributes not mapped**. You can do the same in the Source attributes table (for the incoming fields). You can see that there is one attribute that is not mapped, more specifically attribute FULL_NAME from target.
![](./images/attributes-not-mapped.png " ")

43. Now drag and drop **FULLNAME** under Source attributes to **FULL_NAME** under Target attributes. All attributes are now mapped.
![](./images/map-fullname.png " ")

44. Click **View Rules** to filter and view the applied Rules.
![](./images/view-rules.png " ")
![](./images/rules.png " ")

45. You have now completed the data flow. Click on **Validate** to see the validation output. There shouldn't be any warnings or errors.
![](./images/validate.png " ")

46. To save the data flow, click **Save**.
![](./images/save-df.png " ")

## **STEP 3:** Create a Data Flow - 2
To further explore the capabilities of Data Flows in OCI Data Integration, you will now create **a new Data Flow** with different transformation rules.

This Data Flow will load data from **multiple source files** using File Patterns functionality in OCI Data Integration. After, you will do transformations on the data and later load the data in **multiple target tables**, based on the region. We will take advantage of the **Split operator** in OCI Data Integration.

1. From the Project Details page for `DI_Workshop` project, click on **Data Flows** from the submenu.
![](./images/click-data-flows.png " ")

2. Click **Create Data Flow**.
![](./images/click-create-df.png " ")

3. The data flow designer opens in a new tab. In the **Properties panel**, for **Name**, enter `Load Employees by Region`, and click **Save**.
![](./images/load-emp.png " ")
![](./images/save-button.png " ")


4. You will add your **Source operator**. You add source operators to identify the data entities to use for the data flow. From the Operators panel on the left, drag and drop a Source operator onto the canvas.
![](./images/source-op-new.png " ")

5.  On the canvas, select **SOURCE_1** operator. The Properties panel now displays the details for this operator.
In the Details tab, click Select next to each of the following options to make your selections:
  - For **Data Asset**, select `Object_Storage`
  - For **Connection**, select `Default Connection`
  - For **Schema**, select your **compartment** and then your **bucket**. For the purposes of this tutorial, **Object Storage** serves as the source data asset, this is why you select your bucket here
  - For **Data Entity**, click on **Browse by Pattern**.
  ![](./images/browse-pattern.png " ")

  Write the file pattern `EMPLOYEES\_*` and click **Search**. All files from your Object Storage bucket that are found that match this pattern are now displayed: you have three files for employees. Click on **Select Pattern**.
  ![](./images/employees-pattern.png " ")

  For **File Type**, choose **CSV** and leave the defaults for the other fields that appear. Click **Select**.
  ![](./images/source-entity.png " ")

  In the end, your details for the source operator should look like this:
  ![](./images/pattern-source.png " ")

6. Drag and drop a **Distinct operator** on the data flow canvas. We use the distinct operator to return distinct rows with unique values. Connect **EMPLOYEES__** source to the **DISTINCT_1** operator.
![](./images/add-distinct.png " ")

7. Drag and drop an **Expression operator** on the data flow canvas. Connect the **DISTINCT_1** operator to the new **Expression** operator.
![](./images/new-expres.png " ")

8. In the Properties panel for **EXPRESSION\_1** operator, rename the Identifier to **TRANSFORM\_DATAYPES**.
![](./images/transform-datatypes.png " ")

9. You will now add a **new expression**. Still in the Properties panel, click on **Add Expression**.
![](./images/add-exp.png " ")

10. In the **Add Expression** panel:
  - **Rename** the expression to `BIRTH_DATE` in the Identifier field
  - Change **Data Type** to `DATE`
  - Enter `TO\_DATE(EXPRESSION\_1.EMPLOYEES\__.Date\_of\_Birth, 'MM/dd/yyyy')` in the **expression** box. This function will covert the **STRING** value of birth date from the source files to a **DATE** data type value, in the specified format.
  You can also find this functions in **Functions** tab, under **Date/Time** section and select it from there. Attributes can be added from **Incoming** tab, by highlighting a function's placeholders and then double-click or drag and drop attributes from the Incoming list to create an expression.
  - Click **Add**.

![](./images/new-exp-details.png " ")


11. Your expression for **BIRTH_DATE** is now displayed. Click again on **Add Expression** to add a new one.
![](./images/add-new-exp.png " ")

12. In the **Add Expression** panel:
  - **Rename** the expression to `YEAR_OF_JOINING` in the Identifier field
  - Change **Data Type** to `NUMERIC`
  - Enter `TO\_NUMBER(EXPRESSION\_1.EMPLOYEES\__.Year\_of\_Joining)` in the **expression** box. This function will transform your string value of year of joining from the files to a number value.
  - Click **Add**.

![](./images/new-num-exp.png " ")


13. The expressions for the **TRANSFORM\_DATAYPES** operator should now look like this:
![](./images/expressions-second-df.png " ")

14. Drag and drop an **Expression operator** on the data flow canvas. Connect the **TRANSFORM\_DATAYPES** operator to the new **Expression** operator.
![](./images/new-expression-df.png " ")

15. In the Properties panel for the new **EXPRESSION\_1 operator**, rename the Identifier to **EMPLOYEE_AGE_AND_PHONE**.
![](./images/employee-age.png " ")

16. You will now add a new expression. Still in the Properties panel, click on **Add Expression**.
![](./images/add-exp-new.png " ")

17. In the **Add Expression** panel:
  - **Rename** the expression to `EMPLOYEE_AGE` in the Identifier field
  - Change **Data Type** to `NUMERIC`
  - Enter

  `CASE WHEN DAYOFYEAR(CURRENT_DATE)>=DAYOFYEAR(EXPRESSION_1.EXPRESSION_1.BIRTH_DATE) THEN TRUNC(YEAR(CURRENT_DATE)-YEAR(EXPRESSION_1.EXPRESSION_1.BIRTH_DATE)) ELSE TRUNC(YEAR(CURRENT_DATE)-YEAR(EXPRESSION_1.EXPRESSION_1.BIRTH_DATE)-1) END`
  in the **expression** box.
  This function will calculate the age of the employee, by doing a minus between the current date and his birthdate. CASE WHEN function returns the value for which a condition is met.
  *Note: In case the attributes in the expression don't get automatically highlighted, please replace them, by highlighting in the expression's placeholders and then double-click or drag and drop attributes from the Incoming list.*
  - Click **Add**.

![](./images/new-exp-case.png " ")


18. You will now add a new expression in the same operator. Still in the Properties panel, click on **Add Expression**.
![](./images/add-expression-phone.png " ")

19. In the **Add Expression** panel:
  - **Rename** the expression to `PHONE_NO` in the Identifier field
  - Leave **Data Type** to `VARCHAR`
  - Enter `COALESCE(EXPRESSION_1.EMPLOYEES__.Phone_No_, 'Phone No Not Available')`	in the **expression** box
  This function will fill in the null values for phone number with string `Phone No Not Available`.
  - Click **Add**.

![](./images/phone-no-exp.png " ")


20. The two expressions you defined for this operator are now displayed. Click on **Attributes** tab.
![](./images/attributes-tab.png " ")

21. Check the following two fields: **EMPLOYEES\_\_.Age\_in\_Yrs\_**, **EMPLOYEES\__.Year\_of\_Joining**. We will exclude these fields from this operator.
![](./images/check-fields.png " ")

22. Click on **Actions** and then on **Exclude by selection**.
![](./images/exclude-selection.png " ")

23. The fields are now excluded. Click on View Rules to see the rules you defined.
![](./images/rules-exclusions.png " ")

24. Click on Data tab of the EMPLOYEE_AGE_AND_PHONE operator.
![](./images/data-tab-employee.png " ")

25. Scroll to the right until you get to attribute "EXPRESSION_1.EMPLOYEES__.Region". Click on it and a Data Profile window will appear. We can see that we  have employee data from 4 regions: Northeast, West, South, Midwest. You will split the employee data into multiple target tables based on the region.
![](./images/region-profile.png " ")

26. Drag and drop a Split operator on the data flow canvas. Connect the EMPLOYEE_AGE_AND_PHONE operator to the new Split operator. Use the split operator to divide one source of input data into two or more output ports based on split conditions that are evaluated in a sequence. Each split condition has an output port. Data that satisfies a condition is directed to the corresponding output port.
![](./images/split-op.png " ")

27. In the Properties bar of the Split Operator, we will rename it to SPLIT_BY_REGION and we will leave the defaults Match option (First matching condition - It means that data that matches the first condition should be removed from further processing by other conditions).
![](./images/split-region.png " ")

28. Still in Properties bar of the Split Operator, click on Add in Conditions section.
![](./images/add-cond.png " ")

29. In Add Split Condition page:
* Enter Identifier "WEST_MIDWEST_REGION"
* For condition enter SPLIT_1.EMPLOYEES__.Region IN ('Midwest','West')
* Click Save Changes.
![](./images/midwest-cond.png " ")

30. The first split condition you defined is now displayed. After all conditions in the split operator have been evaluated during run-time, data that does not meet a condition is directed to the Unmatched output port. The Split operator properties should look like in this picture:
![](./images/split-op-prop.png " ")

31. Drag and drop a target operator. Connect the WEST_MIDWEST_REGION output of the Split operator to the TARGET_1 operator.
![](./images/first-target.png " ")

32. In the properties for TARGET_1 operator:
* Change to Merge Integration Strategy
* For Data Asset, select Data_Warehouse
* For Connection, select Beta connection
* For Schema. select Beta
* For Data Entity, select EMPLOYEES_WEST_MIDWEST (this target table was created with the prerequisites SQL script you ran on the ADW)
* For Staging Location, select your Object Storage bucket (DI-bucket)
* Merge Key will automatically get populated with the primary key name of the table, from the database
![](./images/employees-west-midwest.png " ")

33. Go to Map tab of the EMPLOYEES_WEST_MIDWEST target operator. You can see that there are 4 attributes that were not mapped automatically in the target.
![](./images/attr-not-mapped.png " ")

34. Manually map the Not Mapped attributes from the target:
* Drag and drop E_Mail from source to EMAIL attribute from target
* Drag and drop Father_s_Name from source to FATHERS_NAME attribute from target
* Drag and drop Mother_s_Name from source to MOTHERS_NAME attribute from target
* Drag and drop Last__Hike from source to LAST_HIKE attribute from target
You are now finished mapping the attributes to the EMPLOYEES_WEST_MIDWEST target table.
![](./images/manual-map.png " ")

35. Drag and drop another target operator. Connect the UNMATCHED output of the Split operator to the TARGET_1 operator. For Properties, do the same as in step 32 but select Data Entity EMPLOYEES_NORTHEAST_SOUTH. Make sure you also map all of the columns, same as in step 34. Entries that don't match the previous split condition will refer to Unmatched condition.
![](./images/northeast-south.png " ")

39. The design of our Data Flow is now ready. Click on Validate. The result in the Global Validation window displays no Errors and no Warnings.
![](./images/validate-df.png " ")

40. Click on Save and Close.
![](./images/save-close-button.png " ")

## **STEP 4:** Create Integration Tasks
Integration tasks in OCI Data Integration let you take your data flow design and choose the parameter values you want to use at runtime.
1. From your Workspace home page of OCI Data Integration, click Open tab (plus icon), and then select Projects.
![](./images/home-projects.png " ")

2. On the Projects page, select the project you have been working on for this workshop, DI_Workshop.
![](./images/select-project.png " ")

3. On the DI_Workshop Project Details page, from the submenu, click Tasks.
![](./images/click-tasks.png " ")

4. Click Create Task, and then select Integration.
![](./images/integration-task.png " ")

5. The Create Integration Task page opens in a new tab. On this page:
- Change the Name to "Load Customers Lab" and enter the optional Description if you wish to. The value in the Identifier field is auto-generated based on the value you enter for Name.
- In the Data Flow section, click Select. In the Select a Data Flow panel, select "Load Customers and Revenue Data", and then click Select.
![](./images/select-df.png " ")
- The Data Flow will be validated after the selection and the result should be displayed as "Successful".
- Click Save and Close.
![](./images/integration-task-save.png " ")

6. From the DI_Workshop project section Tasks, you will now create an Integration Task for your second Data Flow. Click Create Task and then select Integration.
![](./images/integration-task.png " ")

7. The Create Integration Task page opens in a new tab. On this page:
- Change the Name to "Load Employees by Regions" and enter the optional Description if you wish to. The value in the Identifier field is auto-generated based on the value you enter for Name.
- In the Data Flow section, click Select. In the Select a Data Flow panel, select "Load Employees by Region", and then click Select.
- The Data Flow will be validated after the selection and the result should be displayed as "Successful".
- Click Save and Close.
![](./images/save-close-int-task.png " ")

## **STEP 5:** Create a Data Loader task
A data loader task helps you load diverse data set into data lakes, data marts, and data warehouses. You can create a data loader task from the Console or by using the API, and configure transformations to cleanse and process data while it gets loaded into a target data asset. A data loader task takes a source data entity, applies transformations (optional), and then loads the transformed data into a new target data entity, or updates an existing data entity. A data loader task supports transformations at the metadata and data levels.

1. From your Workspace home page of OCI Data Integration, click Open tab (plus icon), and then select Projects.
![](./images/home-projects.png " ")

2. On the Projects page, select the project you have been working on for this workshop, DI_Workshop.
![](./images/select-project.png " ")

3. On the DI_Workshop Project Details page, from the submenu, click Tasks.
![](./images/click-tasks.png " ")

4. Click Create Task, and then select Data Loader.
![](./images/data-loader.png " ")

5. On the Create Data Loader Task page that pops up, for Name, enter "Load Revenue Data into Data Warehouse".
![](./images/loader-name.png " ")

6. In the Source section, click Select.
![](./images/select-source.png " ")

7. In the Select Source page that pops up, select the following values:
* Data Asset: Object_Storage
* Connection: Default Connection
* Compartment: DI-compartment (the Compartment in which you have uploaded your REVENUE.CSV file)
* Schema: Your Object Storage bucket (DI-bucket)
* Data Entity: Click "Browse by Name" and then select REVENUE.csv
* File Type: Set to csv. Then leave the default settings as-is in all the remaining fields
* Click Select.
![](./images/loader-file.png " ")

8. In the Configure Transformations section, click Configure.
![](./images/configure-transf.png " ")

9. The Configure Transformations panel opens, showing the metadata information of the data entity and its attributes. You can also view sample data in the Data tab.
![](./images/loader-attributes.png " ")

10. Click Data to navigate to the Data tab, then locate and select SRC_ORDER_NUMBER.
A panel displays, showing the Data Profile and the Attribute Profile for SRC_ORDER_NUMBER. Null Data Percent for SRC_ORDER_NUMBER is at 100%.
![](./images/src-order-num.png " ")

11. From the transformations icon (three dots) for SRC_ORDER_NUMBER, select Null Fill Up.
![](./images/null-fill-up.png " ")

12. In the Null Fill Up dialog, do the following:
- Enter "Not Available" in the Replace by String field.
- Do not select Keep Source Attributes.
- Leave the Name as-is.
- Click Apply.
![](./images/null-new.png " ")

13. After the Data tab refreshes, use the horizontal scrollbar to scroll to the end of the dataset where the updated SRC_ORDER_NUMBER column is. Notice the values for SRC_ORDER_NUMBER have been replaced by the string you entered.
![](./images/new-field.png " ")

14. In the Data tab, look for attribute ORDER_DTIME2_TIMEZONE by scrolling to the right. Click on the transformation icon (three dots) for ORDER_DTIME2_TIMEZONE, and then select Rename.
![](./images/rename-attr.png " ")

15. In the Rename dialog box, enter a new name for the attribute "ORDER_DTIME2_TIMEZONE". For this workshop, enter "ORDER_TIMEZONE" then click Apply.
![](./images/rename-attribute-loader.png " ")

16. Click the Transformations icon next to the data entity name.
![](./images/transformations.png " ")

17. You can review the list of transformations that are applied to the source dataset. If you would want to remove a transformation, you could click the X icon next to a transformed attribute name. For now close the Configure Transformations panel, click OK.
![](./images/final-transf.png " ")

18. The number of transformation rules applied is shown in the Configure Transformations section.
![](./images/transf-no.png " ")

19. In the Target section, select the Create New Entity check box, and then click Select.
![](./images/loader-tgt.png " ")

20. In the Select Target page, select the following values:
- Data Asset: Data_Warehouse
- Connection: Beta Connection
- Schema: BETA
- Data Entity: Enter "REVENUE_TARGET" for the new entity you're going to create.
- Under Staging Location, select the Object_Storage data asset
- Select the default connection for Object Storage
- Select your DI compartment name
- Select your DI bucket.
- Click Select to complete selecting the target.
![](./images/loader-tgt-all.png " ")

21. The Target section in the Data Loader task now displays your selections for the target. Click Save and Close.
![](./images/loader-save.png " ")


## **STEP 6:** Create a SQL task
A SQL task lets you run a SQL object in pipeline. Currently, the only SQL objects you can run are stored procedures. You create a SQL task by selecting a stored procedure. The stored procedure must exist in the data source that's associated with a data asset already created in your workspace. The variables defined in a stored procedure are exposed as input, output, and in-out parameters in a SQL task.
When you create a SQL task, you can configure values for input parameters only. If input parameters are configured in a SQL task, you can override the default values when you configure the SQL task in a pipeline, and when you run a pipeline that includes the SQL task. In a pipeline, downstream tasks and operations can use the outputs from an upstream SQL task.

1. From your Workspace home page of OCI Data Integration, click Open tab (plus icon), and then select Projects.
![](./images/home-projects.png " ")

2. On the Projects page, select the project you have been working on for this workshop, DI_Workshop.
![](./images/select-project.png " ")

3. On the DI_Workshop Project Details page, from the submenu, click Tasks.
![](./images/click-tasks.png " ")

4. Click Create Task, and then select SQL.
![](./images/create-sql-task.png " ")

5. On the Create SQL Task page, enter:
* Name: You can use `Procedure DWH Load Stats`
*Note: The Identifier field is a system-generated value based on what you enter for Name. You can change the value, but after you save the task, you cannot change the value again.*
* Description (optional)
* Project DI_Workshop is auto-populated because we're creating this task from project details page
![](./images/sql-task-input.png " ")

6. In the SQL section, click Select.
![](./images/select-button.png " ")

7. In the Select SQL page:
* Select the Data Asset: Choose you ADW data asset ("Data_Warehouse")
* Select the Connection: Choose the Beta Connection
* Select the Schema: BETA schema on your ADW
* Select the Stored Procedure: Choose the OCIDI_RESULT procedure.
![](./images/sql-proc.png " ")

8. Review the list selections for the SQL task, then click Done.
![](./images/done-button.png " ")

9. In the Configure Parameters section, click Configure to view or configure values for the stored procedure parameters. The number of parameters is shown next to Parameters Configured.
![](./images/config-params.png " ")

10. In the Configure Stored Procedure Parameters page, review the list of parameters in the stored procedure. Only input parameters can be configured. You can see here the input parameter IN_DI_RESULT from the procedure you're using.
* In the row of the input parameter value for IN_DI_RESULT, click Configure.
![](./images/config-in-par.png " ")
* In the Edit Parameter panel, enter value "SUCCESS" (without any apostrophes) for that input parameter and click Save Changes.
![](./images/in-param.png " ")
* Click Done.
![](./images/done-param.png " ")

11. In the Validate Task section, click Validate to check for errors and warnings in the configured parameter values. When validation is completed, a Successful message should appear near Validation.
![](./images/validate-sql.png " ")

12. Click Save and Close.
![](./images/save-close.png " ")

## Learn More

*(optional - include links to docs, white papers, blogs, etc)*

* [URL text 1](http://docs.oracle.com)
* [URL text 2](http://docs.oracle.com)

## Acknowledgements
* **Author** - <Name, Title, Group>
* **Contributors** -  <Name, Group> -- optional
* **Last Updated By/Date** - <Name, Group, Month Year>
* **Workshop (or Lab) Expiry Date** - <Month Year> -- optional, use this when you are using a Pre-Authorized Request (PAR) URL to an object in Oracle Object Store.
