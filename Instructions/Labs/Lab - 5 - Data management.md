---
lab:
    title: 'Lab 5: Import data using Data Management'
    module: 'Learning Path 05: Migrate data and go live with finance and operations apps'
---


**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**

# Lab 5: Import data using Data Management

## Change Record

<html>
<table><tr><th>Version</th><th>Date</th><th>Change</th></tr>
<tr><td>1.0</td><td>23 Aug 2024</td><td>Initial release</td></tr>
<tr><td>1.1</td><td>10 Dec 2024</td><td>Workaround for expired certificate</td></tr>
<tr><td>1.2</td><td>15 Jan 2025</td><td>Added business scenario</td></tr>
<tr><td>1.3</td><td>19 Feb 2025</td><td>Added The Why</td></tr>
<tr><td>1.4</td><td>21 Aug 2025</td><td>App version has been updated to 10.0.41</td></tr>
<tr><td>1.5</td><td>14 Oct 2025</td><td>Instruction cleanup</td></tr>
<tr><td>1.6</td><td>09 Feb 2026</td><td>Clarifying instruction cleanup</td></tr>
</table>
</html>

## The Why

Effective data management is the backbone of any successful business operation, ensuring that data is accurate, accessible, and actionable. This hands-on lab will teach you how to manage data within Microsoft Dynamics 365 Finance and Operations, a critical skill for maintaining data integrity and supporting business intelligence efforts. By mastering these techniques, you'll be able to streamline data processes, enhance data quality, and provide valuable insights that drive informed decision-making. This practical knowledge will empower you to handle complex data management tasks with confidence, ultimately contributing to the efficiency and success of your organization.


## Business scenario

**Business Scenario**: Imagine you're a Dynamics 365 finance and operations apps administrator for a manufacturing company. You're facing challenges in managing your ever-growing data volume, including limited storage capacity, data inconsistency, and compliance risks.

**How can the Hands-on Exercise Help?** The hands-on exercise you linked provides a step-by-step guide on how to use the data management tools to address these challenges. By following the exercise, you'll learn how to effectively manage your data, optimizing storage usage, improving data quality, and mitigating compliance risks. This will ensure the continued smooth operation of your system and provide a reliable foundation for data-driven decision-making within your manufacturing company.


## Objective

This lab consists of several exercises.

Requirements are a working development virtual machine (VM) with access to the
finance and operations apps and Microsoft Office Excel.

In the first exercise, you’ll prepare to use Data Management by:

-   Refreshing the entity list.

-   Validating the working directory and access for service accounts.

-   Setting the **Ignore** error to yes to enable data to import with errors to
    a staging table.

-   Setting the **Create error file** to yes.

-   Setting **Remove duplicates** to yes to allow duplicates to import to a
    staging table, but not to have them updated in the table.

In the second exercise, you’ll prepare templates for the Data Management
framework, and then in the third exercise, you’ll import an Excel sheet with
data, which requires an Excel sheet with correct column names.

## Exercise 1: Prepare Data Management parameters

*Note:* If you get a "Your connection isn't private" error on browser opening, then select the **Advanced** link, select to **Continue**, then wait 2-3 minutes.

To prepare for configuration of Data Management parameters:

1.  In the user interface, select the **Data management** workspace, and then select the **Framework parameters**.

2.  Select the **Entity settings** tab, and then select **Refresh entity list**
    to refresh data entities in the system. Notice that data entities are now
    updated in the background as an asynchronous job. Get this started, as it takes several minutes.

    ![A screenshot of Data import/export framework parameters where we find the Refresh entity list bottom.](media/L5P01.png)

3.  In the **Framework parameters**, navigate to the **General** tab, and then
    in the **Shared working directory** group, enter **c:\\temp\\dixf** for the
    path.

4.  Select **Validate** to confirm that the service account has access to the
    folder, and then configure the following parameters on the **General** tab,
    then **Save**:

    -   Ignore error: **Yes**

    -   Create error file (if available): **Yes**

    -   Remove duplicates: **Yes**

## Exercise 2: Prepare templates for Data Management

To prepare your templates to use Data Management:

1.  In the **Navigation pane**, select **Workspaces**, select **Data
    management**, and then select the **Templates** tile.

2.  Select the **Load default templates** action pane item.

3.  Find and select **140 – Accounts receivable**, select **Load selected**, and
    then wait for the **140 – Accounts receivable** template to load. When it
    completes you will see entities in the Entities list. (If you don't, then the entity
    list has probably not refreshed yet.)

    ![A screenshot of 140 - Account receivable template loaded.](media/L5P02.png)

5.  In the **Entities** list, **Select all**, and then navigate to **Customer
    groups**, and clear the **Customer groups** entity selection.

6.  Navigate to **Sales order pools**, clear the **Sales order pools** entity selection,
    and then select **Remove entity** at the entity list action bar. This will remove all entities
    _except for_ **Customer groups** and **Sales order pools**.

7.  Select **Yes** for the **Are you sure you want to delete all marked
    records** option, and then verify that only **Customer groups** and **Sales
    order pools** entities remain:

    ![A screenshot of Customer groups and Sales order pools in our template.](media/L5P03.png)

## Exercise 3: Create an import project

To create an import project:

1.  In the **Navigation pane**, select **Workspaces**, and then select **Data
    Management**.

2.  Select the **Export** tile to create an Excel sheet that provides the
    correct naming for columns.

3.  Enter **Group and pool** in the **Group name** field, and then enter
    **Customer group and order pools** in the **Description** field.

4.  In **Selected entities**, select **Add template**, and then in the **Copy
    from template** field, select the **140 – Account receivable** template
    which you created in Exercise 2.

5.  In the **Target data format** field, select **EXCEL**, and then select
    **OK**.

6.  In the upper action pane, select **Export now** (rather than **Export**) and wait to see the
    Execution summary. (Make sure you select Export now to run it in
    interactive mode.)
![A screenshot of a successful data export.](media/L5P04.png)

7.  Under **Entity processing status**, select **Download file** for **Sales
    order pools**. 

9.  For **Entity procession status**, select **Download file** for **Customer
    groups**. 

10.  Open **File Explorer** on your VM, and then open the Excel file for **Sales
    order pools**. You can **Close** the Microsoft Office Activation Wizard if it appears and
    **Enable Editing**.
![A screenshot of exported Sales order pools.](media/L5P05.png)

11.  Right-click column **A** to open the context menu, select **Format Cells**,
    and select OK.

12.  For row **6**, enter ‘**02** for the **POOLID** column.

13.  For row **6**, enter **My order pool** in the **POOLNAME** column.

14.  For row **7**, enter ‘**05** in the **POOLID** column.

15.  For row **7**, enter **My other order pool** in the **POOLNAME** column
    ![A screenshot of Excel file for Sales order pools with two new rows.](media/L5P06.png)

16.  Close **Excel** and select **Save** when prompted.

17.  Go back to Microsoft Edge and the finance and operations apps, and in the
    **Navigation pane**, select Workspaces and **Data management**.

18.  Select the **Import** tile, and then enter **Import Group and Pool** in the
    **Group name** field.

19.  Enter **Import Customer group and order pools** in the **Description**
    field.

20. In **Selected entities**, select **Add file**, and then in **Source data
    format**, select **EXCEL**.

21. In **Entity name**, select **Sales order pools**, and then select **Upload
    and add**.

22. Navigate to the **Downloads** folder, and then select the Excel file for
    **Sales order pools**.

23. When the screen refreshes, select **Customer groups** in **Entity name**, and then select **Upload and
    add**.

24. Navigate to the **Downloads** folder, and then select the **Excel** file for
    **Customer groups**.

25. Select **Close**, and then select **Import now** from the action pane, and wait for the import to finish.
![A screenshot of import with partially succeeded.](media/L5P07.png)   

26.  Select **View execution log** in the action pane, and then verify in the log
    text that two records didn’t add. This is because of a duplicate.
![A screenshot of the log for Sales order pools import.](media/L5P08.png)

27.  Open **File Explorer** on your VM, navigate to the **Downloads** folder, and
    then open the Excel file for **Sales order pools**.

28.  On row **6**, enter ‘**06** for the **POOLID**.

29.  Close **Excel**, and then select **Save** when prompted.

30.  Go back to Microsoft Edge and the finance and operations apps, and in the
    navigation pane, select **Workspaces**, and then select **Data management**.

31.  Select the **Import Group and Pool** Data project, select **Remove Entity**
    for removing Sales order pools data entity from the list, and then select
    **Add file**.

32.  The source data format is EXCEL.

33.  In **Entity name**, select **Sales order pools**, and then select **Upload
    and add**.

34.  Navigate to the **Downloads** folder, and then select the Excel file for
    **Sales order pools**.

35.  Select **Close**, and the updated Excel file will be ready to import.

36. Select **Import now**, and then wait for the import to finish.

37. The **Execution Status** should change to **Succeeded**.

38. Select **View execution log**, and then verify that there are no errors.




