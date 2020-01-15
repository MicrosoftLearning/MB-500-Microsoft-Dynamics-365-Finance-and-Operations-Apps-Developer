**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**

**Lab 3 – Data Structure Development**

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

Task 1: Base Enum: Customer Tier
--------------------------------

1.  Open Visual Studio as administrator, and DynamicsDevProject in Solution
    Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select Base Enum under **Dynamics 365 Items \> Data Types**

4.  Create a new Enum DDTCustomerTier (Label: *Customer Tier*) and add the
    following Enum elements (in Designer, right click on it and select New
    Element) with the same label

    a.  None

    b.  Silver

    c.  Gold

   It's important to do them in this order so that None is the default, which
   is value 0.

Task 2: EDT: Airport Code
-------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select EDT String under **Dynamics 365 Items \> Data Types**

4.  Create a new EDT DDTAirportCode (Label: *Airport* c*ode*)

Task 3: EDT: Flying Miles
-------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select EDT Integer under **Dynamics 365 Items \> Data Types**

4.  Create a new EDT DDTFlyingMiles (Label: *Flying miles*)

Task 4: Table: Tier Range
-------------------------

1.  Save all, so that the EDTs are available for the table

2.  Open DynamicsDevProject in Solution Explorer

3.  Right click on the project and select **Add \> New Item**

4.  Select Table under **Dynamics 365 Items \> Data Model**

5.  Create a new table DDTTierRange (Label: *Tier wise Mile Range*)

6.  Add the following fields in the table

    a.  CustTier

        i.  Enum Type: DDTCustomerTier

    b.  FromMiles

        i.  Extended Data Type: DDTFlyingMiles

        ii.  Label: *From miles*

    c.  ToMiles

        i.  Extended Data Type: DDTFlyingMiles

        ii.  Label: *To miles*

7.  Add new index CustTierIdx

    a.  Field: CustTier

    b.  Allow Duplicates: No

Task 5: Table: Airport Code
---------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select Table under **Dynamics 365 Items \> Data Model**

4.  Create a new table DDTAirport (Label: *Airport Code*)

5.  Add the following fields in the table

    a.  CityRecId

        i.  Extended Data Type: RefRecId (of type Int64)

        ii.  Label: *City code*

    b.  AirportCode

        i.  Extended Data Type: DDTAirportCode

6.  Add the following field group in the table

    a.  DDTAirportCode

        i.  Label: *Airport code*

        ii.  Field: AirportCode

7.  Add the following Index

    a.  AirportCodeIdx

        i.  Field: AirportCode

        ii.  Allow Duplicates (Property): No

        iii.  Alternate Key (Property): Yes

8.  **Save**, and set the following table properties

    a.  Primary Index: SurrogateKey

    b.  Clustered Index: AirportCodeIdx

    c.  Replacement Key: AirportCodeIdx

9.  Create a new Relation: LogisticsAddressCity

    a.  Related Table: LogisticsAddressCity

    b.  RelationshipType: Association

    c.  Cardinality: ZeroOne

    d.  Related Table Cardinality: ExactlyOne

    e.  On Delete: Cascade

    f.  New Normal Relation: (Right click the relation, select New \> Normal)
        DDTAirport.CityRecId = LogisticsAddressCity.RecId

Task 6: Table: Customer Fly Details
-----------------------------------

1.  Open DynamicsDevProject in Solution Explorer

2.  Right click on the project and select **Add \> New Item**

3.  Select Table under **Dynamics 365 Items \> Data Model**

4.  Create a new table DDTCustFlyDetails (Label: *Customer Fly Details*)

5.  Add the following fields in the table

    a.  CustAccount

        i.  EDT: CustAccount (Hint: You can select View \> Application Explorer,
            and navigate to AOT \> Data Types \> Extended Data Types \>
            CustAccount, then drag CustAccount to the Fields node of our new
            table in the designer pane)

    b.  FlyCount

        i.  EDT: Counter

    c.  FlyingDate

        i.  EDT: TransDate

        ii.  Label: *Flying Date*

        iii.  Mandatory: Yes

    d.  FlyFrom

        i.  EDT: RefRecId

        ii.  Label: *From city*

        iii.  Mandatory: Yes

    e.  FlyTo

        i.  EDT: RefRecId

        ii.  Label: *To city*

        iii.  Mandatory: Yes

    f.  FlyingMiles

        i.  EDT: DDTFlyingMiles

        ii.  Mandatory: Yes

6.  Create a new index: CounterIdx

    a.  Fields: CustAccount, FlyCount

    b.  Allow Duplicates (property): No

    c.  Alternate Key: Yes

7.  Create another index: CustFlyingIdx

    a.  Fields: CustAccount, FlyingDate

    b.  Allow Duplicates (property): Yes

8.  Create a new Relation: CustTable

    a.  Related Table: CustTable

    b.  RelationshipType: Association

    c.  Cardinality: ZeroMore

    d.  Related Table Cardinality: ZeroOne

    e.  On Delete: Restricted

    f.  New normal relation: DDTCustFlyDetails.CustAccount =
        CustTable.AccountNum

9.  Create a new Relation: AirportFrom

    a.  Related Table: DDTAirport

    b.  RelationshipType: Association

    c.  Cardinality: ZeroMore

    d.  Related Table Cardinality: ZeroOne

    e.  On Delete: Restricted

    f.  New normal relation: DDTCustFlyDetails.FlyFrom = DDTAirport.RecId

10. Create a new Relation (or copy the previous and make small changes):
    AirportTo

    a.  Related Table: DDTAirport

    b.  RelationshipType: Association

    c.  Cardinality: ZeroMore

    d.  Related Table Cardinality: ZeroOne

    e.  On Delete: Restricted

    f.  New normal relation: DDTCustFlyDetails.FlyTo = DDTAirport.RecId

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

    a.  Label: *Tier*

    b.  Add field: DDTCustomerTier

Check Output
============

   Save all, then right click on your solution and select Build solution. This
   takes a minute or two. Verify that there are no errors. (There will be
   warnings, due to best practices.)

   Your solution should look similar to this:

![Solution DynamicsDevSolution
DynamicsDevProject
Base Enums: DDTCustomerTier
EDT Integers: DDTFlyingMiles
EDT Strings: DDTAirportCode
Table Extensions: CustTable.DynamicsDevTraining
Tables: DDTAirport, DDTCustFlyDetails, DDTTierRange](Images/Lab3CO.png)


