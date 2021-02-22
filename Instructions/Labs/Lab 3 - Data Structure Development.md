---
lab:
    title: 'Exercise 01: Data structure development'
    module: 'Module 03: Solution design'
---

**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**

**Lab 3 – Data Structure Development**

Change Record
=============

| Version | Date        | Change                                                                                        |
|---------|-------------|-----------------------------------------------------------------------------------------------|
| 1.0     | 10 Jan 2020 | Initial release                                                                               |
| 1.01    | 22 Jan 2021 | Added instructions re: saving work, resource files, importing and exporting, changing company |
| 1.02    | 29 Jan 2021 | Restored images |

Lab Environment
===============

In order to run this lab, you will need:

-   An all-in-one demo data VM with

    -   Visual Studio installed, and a Visual Studio subscription

    -   Lab 1 – Development Environment Configuration completed

Lab Overview
============

-   Dependency: Lab 1 – Development Environment Configuration should be
    completed

-   Develop Data Models in the newly created project

**Estimated time to complete this lab: 20+ minutes**

Scenario
========

In this lab, we will create some new and extend some existing Data Models, which
we will work on in subsequent labs. These Data Models will capture data related
to customer Flying Details and Tier status.

Exercise 1: Add new Data Models
===============================

In this exercise, you will add some data objects which will be used in
subsequent lab exercises.

Prerequisite tasks
------------------

-   There are resource files available which will be needed at various points in
    the course. They may already be provided for you on your training VM;
    otherwise please verify access to <http://aka.ms/mb500labresources>.

-   You will want to save your work. Training VMs typically do not live for the
    duration of the course and you will need to start with a new machine. The
    labs build off each other so need to be saved. Please verify access to your
    [OneDrive](https://onedrive.live.com/) or a cloud-based repository of your
    choice.

-   If your VM expires prior to the end of the course, you’ll want to note:

    -   **Code**: export your code at the end of each lab and save it to your
        cloud storage, and then import it when you begin the next one. Make sure
        to import the DDT solution before the MLA solution (created later),
        because the latter depends upon the former.

    -   **Data** should also be recreated as needed.

    -   **Settings (options)** are not imported and should be set again if
        desired.

-   When you log in to your application, the company should be changed to USMF.

Task 1: Base Enum: Customer Tier
--------------------------------

1.  Open Visual Studio as administrator, and DynamicsDevProject in Solution
    Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select Base Enum under **Dynamics 365 Items \> Data Types**

4.  Create a new Enum **DDTCustomerTier** (Label: **Customer Tier**) and add the
    following Enum elements (in Designer, right click on it and select New
    Element) with the same label

    1.  None

    2.  Silver

    3.  Gold

   It’s important to do them in this order so that None is the default, which
   is value 0.

Task 2: EDT: Airport Code
-------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select EDT String under **Dynamics 365 Items \> Data Types**

4.  Create a new EDT **DDTAirportCode** (Label: **Airport code**)

Task 3: EDT: Flying Miles
-------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select EDT Integer under **Dynamics 365 Items \> Data Types**

4.  Create a new EDT **DDTFlyingMiles** (Label: **Flying miles**)

Task 4: Table: Tier Range
-------------------------

1.  Save all, so that the EDTs are available for the table

2.  Open DynamicsDevProject in Solution Explorer

3.  Right click on the project and select **Add \> New Item**

4.  Select Table under **Dynamics 365 Items \> Data Model**

5.  Create a new table **DDTTierRange** (Label: **Tier wise Mile Range**)

6.  Add the following fields in the table

    1.  CustTier

        1.  Enum Type: DDTCustomerTier

    2.  FromMiles

        1.  Extended Data Type: DDTFlyingMiles (of type Int64)

        2.  Label: *From miles*

    3.  ToMiles

        1.  Extended Data Type: DDTFlyingMiles (of type Int64)

        2.  Label: *To miles*

7.  Add new index CustTierIdx

    1.  Field: CustTier

    2.  Allow Duplicates: No

Task 5: Table: Airport Code
---------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select Table under **Dynamics 365 Items \> Data Model**

4.  Create a new table **DDTAirport** (Label: **Airport Code**)

5.  Add the following fields in the table

    1.  CityRecId

        1.  Extended Data Type: RefRecId (of type Int64)

        2.  Label: *City code*

    2.  AirportCode

        1.  Extended Data Type: DDTAirportCode

6.  Add the following field group in the table

    1.  DDTAirportCode

        1.  Label: *Airport code*

        2.  Field: AirportCode

7.  Add the following Index

    1.  AirportCodeIdx

        1.  Field: AirportCode

        2.  Allow Duplicates (Property): No

        3.  Alternate Key (Property): Yes

8.  **Save**, and set the following table properties

    1.  Primary Index: SurrogateKey

    2.  Clustered Index: AirportCodeIdx

    3.  Replacement Key: AirportCodeIdx

9.  Create a new Relation: LogisticsAddressCity

    1.  Related Table: LogisticsAddressCity

    2.  RelationshipType: Association

    3.  Cardinality: ZeroOne

    4.  Related Table Cardinality: ExactlyOne

    5.  On Delete: Cascade

    6.  New Normal Relation: (Right click the relation, select New \> Normal)
        DDTAirport.CityRecId = LogisticsAddressCity.RecId

Task 6: Table: Customer Fly Details
-----------------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select Table under **Dynamics 365 Items \> Data Model**

4.  Create a new table **DDTCustFlyDetails** (Label: **Customer Fly Details**)

5.  Add the following fields in the table

    1.  CustAccount

        1.  EDT: CustAccount (Hint: You can select View \> Application Explorer,
            and navigate to AOT \> Data Types \> Extended Data Types \>
            CustAccount, then drag CustAccount to the Fields node of our new
            table in the designer pane)

    2.  FlyCount

        1.  EDT: Counter

    3.  FlyingDate

        1.  EDT: TransDate

        2.  Label: *Flying Date*

        3.  Mandatory: Yes

    4.  FlyFrom

        1.  EDT: RefRecId

        2.  Label: *From city*

        3.  Mandatory: Yes

    5.  FlyTo

        1.  EDT: RefRecId

        2.  Label: *To city*

        3.  Mandatory: Yes

    6.  FlyingMiles

        1.  EDT: DDTFlyingMiles

        2.  Mandatory: Yes

6.  Create a new index: CounterIdx

    1.  Fields: CustAccount, FlyCount

    2.  Allow Duplicates (property): No

    3.  Alternate Key: Yes

7.  Create another index: CustFlyingIdx

    1.  Fields: CustAccount, FlyingDate

    2.  Allow Duplicates (property): Yes

8.  Create a new Relation: CustTable

    1.  Related Table: CustTable

    2.  RelationshipType: Association

    3.  Cardinality: ZeroMore

    4.  Related Table Cardinality: ZeroOne

    5.  On Delete: Restricted

    6.  New normal relation: DDTCustFlyDetails.CustAccount =
        CustTable.AccountNum

9.  Create a new Relation: AirportFrom

    1.  Related Table: DDTAirport

    2.  RelationshipType: Association

    3.  Cardinality: ZeroMore

    4.  Related Table Cardinality: ZeroOne

    5.  On Delete: Restricted

    6.  New normal relation: DDTCustFlyDetails.FlyFrom = DDTAirport.RecId

10. Create a new Relation (or copy the previous and make small changes):
    AirportTo

    1.  Related Table: DDTAirport

    2.  RelationshipType: Association

    3.  Cardinality: ZeroMore

    4.  Related Table Cardinality: ZeroOne

    5.  On Delete: Restricted

    6.  New normal relation: DDTCustFlyDetails.FlyTo = DDTAirport.RecId

11. Select the **Save All** icon

Exercise 2: Extend Data Models
==============================

In this exercise, you will extend some standard data models which will be used
in subsequent lab exercises.

Task 1: Table Extension: CustTable
----------------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  In the Application Explorer under Data Model and Tables, search for
    CustTable table

3.  Right click CustTable and select **Create extension**

4.  A new element will be created in Solution Explorer under *Table Extensions*
    folder named CustTable.DynamicsDevTraining

5.  Double click it to open it in Designer

6.  Add new field DDTCustomerTier in CustTable.DynamicsDevTraining by dragging
    the Base Enum DDTCustomerTier and dropping on the Fields node of the
    extended table

7.  Add a new Field group: DDTCustomerTier

    1.  Label: *Tier*

    2.  Add field: DDTCustomerTier

Check Output
============

   Save all, then right click on your solution and select Build solution. This
   takes a minute or two. Verify that there are no errors. (There will be
   warnings, due to best practices.)

![Solution DynamicsDevSolution
DynamicsDevProject
Base Enums: DDTCustomerTier
EDT Integers: DDTFlyingMiles
EDT Strings: DDTAirportCode
Table Extensions: CustTable.DynamicsDevTraining
Tables: DDTAirport, DDTCustFlyDetails, DDTTierRange](Images/Lab3CO.png)
