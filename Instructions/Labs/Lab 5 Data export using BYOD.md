---
lab:
    title: 'Lab 5: Data export using BYOD'
    module: 'Learning Path 05: Migrate data and go live'
---

**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**


# Change Record

<html>
<table><tr><th>Version</th><th>Date</th><th>Change</th></tr>
<tr><td>1.0</td><td>29 Sep 2023</td><td>Initial release</td></tr>
</table>
</html>


# Objective

In this lab, we will export records from a table to an external database. This
external database can be used for reporting purposes or for any other reasons.
In this lab, we already have an on-premises SQL Server instance. Hence, we will
create a database named BYOD in the SQL Server instance. Data from finance and
operations apps will be pushed to the external database BYOD.

# Exercise 1: Configure BYOD


## Task 1: Create a new database

**Note:** *In this task, we will create the new database BYOD in the on-premises SQL Server instance. We will also configure the password of the default SQL Server login ‘sa’. We will need this login and password later in the exercise.*


1.  Open **Microsoft SQL Server Management Studio 18** in your Virtual Machine
    (VM). To open it, you can select the Start icon in the bottom left corner
    and type *“ssms”.*

2.  A **Connect to Server** prompt will appear asking the credential to connect
    to the SQL Server instance.

3.  Select *Windows Authentication* in the **Authentication** field and select
    the **Connect** button.

4.  Under **Object Explorer**, right click the **Databases** node and select
    **New Database.**

5.  Type *BYOD* in the **Database name** field and select the **OK** button at
    the bottom.

6.  A new database *BYOD* will be created.

7.  Expand the **Security** node and again expand the **Logins** node.

8.  Right click on the *sa* login and select the **Properties** option.

9.  In the **Password** and **Confirm password** fields, type *[password]*.

    1.  The password is the same password you used to get into the VM, with the
        user localadmin, or you may ask your instructor. No brackets.

10. Uncheck the **Enforce password policy** field and select the **OK** button
    at the bottom.

11. To check if the new password is working, you can close **SQL Server
    Management Studio** and reopen it.

12. In the **Connect to Server** prompt, select *SQL Server Authentication* in
    the **Authentication** field. Type *sa* and *[password previously
    discussed]* in the **Login** and **Password** field and select the
    **Connect** button.

13. You should be able to get inside the SQL Server with this credential.

## Task 2: Configure the Data entity to be exported

**Note:** *In this task, we will enable the change tracking property of the data entity Customers V3. This will help to configure the incremental data export from the CustTable to the BYOD database.*


1.  Navigate to the finance and operations apps home page and select the **Data
    management** workspace.

2.  Select the **Framework parameters** tile under the **Import/Export** fastTab
    in the **Data management** workspace.

3.  In the **Entity settings** tab page, select **Refresh entity** list.
**Note:** *It may take a few minutes to refresh all data entities*

4.  Select the **Data entities** tile under the **Import/Export** fastTab.

5.  In the Quick Filter box type *Customers V3*.

6.  Select the *Customers V3* entity that appears in the grid.

7.  Select the **Enable primary table** button under the **Change tracking**
    menu in the action pane.

8.  The value of the **Change tracking** field is changed to *Primary table* of
    the record *Customers V3* entity.

## Task 3: Create Azure SQL DB data source

**Note:** *In this task, we will create a target data source of type Azure SQL DB. In Azure hosted instances, we create the external database in Azure SQL. The connection string of the Azure hosted SQL database should be provided while creating the target data source. In this lab, we will provide the connection string of the on-premises SQL database.*


1.  Select the **Configure entity export to database** tile under the
    **Import/Export** fastTab in the **Data management** workspace.

2.  Create a new record by selecting the **New** button in the action pane.

3.  Type *BYOD* in the **Source name** field.

4.  Type *BYOD* in the **Description** field.

5.  In the **Connection string** field type *Data Source=[DB server name],1433;
    Initial Catalog=BYOD; Integrated Security=False; User ID=sa;
    Password=[password previously discussed]*

    1.  The *DB server name* is the root node of **Object Explorer** in the
        **SQL Server Management Studio**.
    2.  Remove all brackets.
    3.  You may **Validate** if you like.

6.  Save the record by selecting the **Save** button in the action pane.

7.  Select the **Publish** button in the action pane.

8.  Select the entity *Customers V3* and select the **Publish** button again in
    the action pane.

9.  In a short time the entity *Customers V3* will be published. You can check
    the **Show published only** check box and find the value of the
    **Published** column is *Yes* for the record *Customer V3* entity.

# Testing

1.  Select the **Export** tile under the **Import/Export** fastTab in the **Data
    management** workspace.

2.  Type *CustExportBYOD* in the **Group name** field.

3.  Select the **Add entity** button in the **Selected entities** fastTab.

4.  Select *Customers V3* in the **Entity name** field.

5.  Select *BYOD* in the **Target data format** field.

6.  Select *Incremental push only* in the **Default refresh type** field.

7.  Select the **Add** button.

8.  Once you get the message “*Customer V3 entity mapping has completed
    successfully*”, select the **Close** button.

9.  In the action pane, select the **Save** button.

10. Select the **Export now** button, under **Export options** in the action
    pane.

11. **Execution summary** page will appear with a “Checked” image in the
    **Execution summary::Export** fastTab.

12. Navigate back to the **SQL Server Management Studio** and expand the *BYOD*
    database under the **Databases** node. You will find a new table
    *CustCustomerV3Staging* will be created under the **Tables** node. Right
    click on *dbo.CustCustomerV3Staging* and select the option **Select Top 1000
    Rows**.
**Note:** *This table is the replica of the staging table which is created when the Customer V3 data entity was created.*


13. You will find all the customer records are exported to this table in the
    *BYOD* database.

14. Navigate to **Module** \> **Accounts receivable** \> **Customers** \> **All
    customers**.

15. Enter a new Customer by entering data into following fields and save the
    record

    1.  **Account**: *Demo01*

    2.  **Name**: *Demo Customer*

    3.  **Customer group**: *10*

16. Navigate back to the **Data management** workspace and select the project
    *CustExportBYOD* in the **All projects** tab page under **Data projects**
    fastTab.

17. Select **Load project** in the toolbar of the **Data project** grid.

18. Select the **Export now** button again, under **Export options** in the
    action pane.

19. **Execution summary** page will appear again with a “Checked” image in the
    **Execution summary::Export** fastTab.

20. Navigate back to **SQL Server Management Studio** and expand the *BYOD*
    database under the **Databases** node. Right click on
    *dbo.CustCustomerV3Staging* under the **Tables** node and select the option
    **Select Top 1000 Rows**.

21. You will find the newly created customer record is also exported to this
    table in the *BYOD* database.

**Note:** *You can create a batch process for this export operation, which will pick up the new or changed records on regular basis and export them to the BYOD database, without any human interaction.*
