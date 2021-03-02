---
lab:
    title: 'Exercise 01: Metadata extension and development'
    module: 'Module 04: AOT elements'
---

**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**

**Lab 4 – Metadata Extension & Development**

Change Record
=============

| Version | Date        | Change                                                           |
|---------|-------------|------------------------------------------------------------------|
| 1.0     | 10 Jan 2020 | Initial release                                                  |
| 1.01    | 22 Jan 2021 | Remove table of contents; update branding; remove LCS references |

Lab Environment
===============

In order to run this lab, you will need:

-   An all-in-one demo data VM with

    -   Visual Studio installed, and a Visual Studio subscription

    -   A browser to run the user interface

    -   Lab 3 – Data Structure Development completed

Lab Overview
============

-   Dependency: Lab 3 – Data Structure Development should be completed

-   Develop & Extend forms

**Estimated time to complete this lab: 30+ minutes**

Scenario
========

In this lab, we will develop/extend some forms, menu items and menus for which
the Data Models were prepared in Lab 3 – Data Structure Development.

First, you need to develop a form “Miles wise Customer Tier”, where we will
capture the required flying miles to attain a specific Customer Tier. You need
to add a menu under Accounts Receivables \> Setup to call this form

You need to develop a form to capture Flight details of Customers, which will
have the travel date, From and To Airport and Miles accumulated in the travel.
This form will later be added as a form part in the Customer Form detail sheet

You need to add a new field Airport Code in the tab City of the form Address
Setup under Organizational Administration \> Global Address Book \> Addresses. A
new table is created for Airport Code with 1:1 relationship with the standard
LogisticsAddressCity table. This is because Airport code has to be unique; and
not all cities in the LogisticsAddressCity table will have an Airport Code.

New field “Customer Tier” is added in the Customer form. Customer Flying Details
is also added as a new tab in the detail sheet of the Customer form.

Exercise 1: Add new Forms
-------------------------

### Task 1: Form: Miles wise Tier Range

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click the project and select **Add \> New Item**

3.  Select **Form** under **Dynamics 365 Items \> User Interface**

4.  Create a new form DDTTierRange

5.  Add DDTTierRange in the Form data sources

    1.  Property: Index: CustTierIdx

    2.  Property: Insert If Empty: No

6.  Right click **Design \| Pattern** \> **Apply pattern** and select **Simple
    List** as form pattern

7.  Right click **Design \| Pattern** and select **New** and add a new Action
    Pane

    1.  Name: TierRangeActionPane

8.  Right click **Design \| Pattern** and select **New** and add a new Group

    1.  Name: FilterGroup

    2.  Pattern: Custom & Quick Filters

    3.  Right click **FilterGroup (Group) \| Pattern** and add a new QuickFilter

        1.  Name: CustTierQuickFilter

9.  Right click **Design \| Pattern** and select **New** and add a new Grid

    1.  Name: CustTierGrid

    2.  Drag the following fields from the data source and add into the grid:

        1.  CustTier

        2.  FromMiles

        3.  ToMiles

### Task 2: Display Menu Item: Mile wise Tier Range

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click the project and select **Add \> New Item**

3.  Select Display Menu Item under **Dynamics 365 Items \> User Interface**

4.  Create a new Display menu item DDTCustTierDisplay

    1.  Object Type: Form

    2.  Object: DDTTierRange

    3.  Label: *Miles wise Tier Range*

### Task 3: Form: Customer Fly Details

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click the project and select **Add \> New Item**

3.  Select Form under **Dynamics 365 Items \> User Interface**

4.  Create a new form DDTCustFlyDetails

5.  Add DDTCustFlyDetails in the Form data sources

    1.  Property: Index \> CustFlyingIdx

    2.  Property: Insert If Empty \> No

6.  Right click **Design \| Pattern** and select **Custom** as form pattern

7.  Right click **Design \| Pattern** and select **New** and add a new Action
    Pane

    1.  Name: FlyDetailsActionPane

    2.  Data Source: DDTCustFlyDetails

    3.  Skip: Yes

    4.  Style: Strip

8.  Right click **FlyDetailsActionPane** and add a new Action Pane Tab

    1.  Name: FlyDetailsActionPaneTab

    2.  Skip: Yes

9.  Add a new Button Group within **FlyDetailsActionPaneTab**

    1.  Name: FlyDetailsActionButtonGroup

    2.  Arrange Method: Vertical

10. Add a new Command Button within FlyDetailsActionButtonGroup

    1.  Name: NewFlyInfo

    2.  Command: New

    3.  Needed Permission: Create

    4.  Text: Add

    5.  Normal Image: New

11. Add a new Command Button within FlyDetailsActionButtonGroup

    1.  Name: DeleteFlyInfo

    2.  Command: DeleteRecord

    3.  Needed Permission: Delete

    4.  Text: Delete

    5.  Normal Image: Remove

12. Add a new Grid under **Design \| Pattern**

    1.  Name: FlyInfoGrid

    2.  Data Source: DDTCustFlyDetails

    3.  Drag the following fields from the data source and add in the Grid:

        1.  FlyCount

        2.  FlyingDate

        3.  FlyFrom

        4.  FlyTo

        5.  FlyingMiles

    4.  If they are not in this order, use the Alt and arrow keys to rearrange
        them

    5.  For the field DDTCustFlyDetails_FlyingMiles, change the property Skip to
        Yes

### Task 4: Display Menu Item: Customer Fly Details Form Part

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click the project and select **Add \> New Item**

3.  Select Display Menu Item under **Dynamics 365 Items \> User Interface**

4.  Create a new Display menu item DDTCustFlyDetailsFormPart

    1.  Object Type: Form

    2.  Object: DDTCustFlyDetails

    3.  Label: *Fly Details*

Save all.

Exercise 2: Extend Standard Form
--------------------------------

### Task 1: Form Extension: LogisticsAddressSetup

1.  Open DynamicsDevProject in Solution Explorer

2.  In the Application Explorer, search under **User Interface \> Forms** for
    the LogisticsAddressSetup form

3.  Right click LogisticsAddressSetup and select **Create Extension**

4.  A new element will be created in Solution Explorer under *Form Extensions*
    folder named LogisticsAddressSetup.DynamicsDevTraining. Double click it to
    open it in Designer.

5.  Add a new Data Source: DDTAirport

    1.  Table: DDTAirport

    2.  Join Source: LogisticsAddressCity

6.  Navigate to **Design \> Tab \> TabPageCity \> GroupCityBody \> GroupCity \>
    CityDetailsBody**

7.  Drag Field Group DDTAirportCode and drop at the above location at the end

### Task 2: Form Extension: CustTable

1.  Open DynamicsDevProject in Solution Explorer

2.  In Application Explorer, search for CustTable form

3.  Right click CustTable and select **Create Extension**

4.  A new element will be created in the Solution Explorer under *Form
    Extensions* folder named CustTable.DynamicsDevTraining

5.  Double click the form to open it in Designer and navigate to Design. Under
    the node, navigate to **Tab \> TabPageDetails \> TabHeader \> TabGeneral \>
    UpperGroup \> Identification**

6.  Drag the DDTCustomerTier FieldGroup from **Data Sources \> CustTable \>
    Field groups** and drop it within *Identification*

7.  Change the Frame Type property of the FormGroupControl DDTCustomerTier to
    None

8.  Under the Design node, navigate to **Tab \> TabPageDetails \> TabHeader**
    and add a new tabpage

    1.  Name: DDTTabFlyDetails

    2.  Pattern: Custom

    3.  Caption: Flying Details

9.  Create a new Form Part under the tab page DDTTabFlyDetails

    1.  Name: FlyingDetailsGridFormPart

    2.  MenuItemName: DDTCustFlyDetailsFormPart

10. Expand FlyingDetailsGridFormPart and Right click Links to create New Field
    relation link

    1.  Name: FlyingDetailsDataLink

    2.  DataSource: CustTable

    3.  DataField: AccountNum

    4.  TargetDataSource: DDTCustFlyDetails

    5.  TargetDataField: CustAccount

### Task 3: Menu Extension: AccountsReceivable

1.  Open DynamicsDevProject in Solution Explorer

2.  In Application Explorer, search for AccountsReceivable menu under User
    Interface \> Menus

3.  Right click AccountsReceivable and select **Create Extension**

4.  A new element will be created in the Solution Explorer under **Menu
    Extensions** folder named AccountsReceivable.DynamicsDevTraining

5.  Open AccountsReceivable.DynamicsDevTraining in the designer to drag the
    display Menu item DDTCustTierDisplay and drop it under **Setup** submenu

### Task 4: Finalize

1.  Build solution.

Check Output
------------

1.  In a browser, in the USMF entity, open **Modules \> Accounts Receivable \>
    Setup \> Miles wise Tier Range**

    1.  Add two records:

| Customer Tier | From Mile | To Mile |
|---------------|-----------|---------|
| None          | 0         | 100     |
| Silver        | 101       | 100000  |

2.  Open **Organization Administration \> Global Address Book \> Addresses \>
    Address setup**

    1.  Select City tab

    2.  Select IND in the Country/Region filter and **Apply filter**

    3.  You should find a new field Airport Code in the right pane

    4.  Add the following values in the Airport Code field:

| City      | Airport Code |
|-----------|--------------|
| Hyderabad | HYD          |
| Delhi     | DEL          |
| Bangalore | BLR          |
| Mumbai    | BOM          |
| Chennai   | MAS          |

3.  Open **Accounts Receivable \> Customers \> All Customers**

    1.  Open Customer DE-001 followed by **Flying Details** fast tab

    2.  Please add the following data:

| Counter | Flying Date | From City | Fly To | Flying Miles |
|---------|-------------|-----------|--------|--------------|
| 1       | 9/1/2019    | DEL       | BOM    | 200          |
| 2       | 9/2/2019    | BOM       | DEL    | 200          |
