---
lab:
    title: 'Exercise 01: Extension framework'
    module: 'Module 07: Frameworks'
---

**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**

**Lab 7 - Extension Framework**

Change Record
=============

| Version | Date        | Change                                                           |
|---------|-------------|------------------------------------------------------------------|
| 1.0     | 10 Jan 2020 | Initial release                                                  |
| 1.01    | 22 Jan 2021 | Remove table of contents; update branding; remove LCS references |

Lab Environment
---------------

In order to run this lab, you will need:

-   An all-in-one demo data VM with

    -   Visual Studio installed, and a Visual Studio subscription

    -   A browser to run the user interface

    -   Lab 5 – Code Extension & Development completed

Lab Overview
------------

-   Dependency: Lab 5 - Code Extension & Development should be completed

-   Implementation of Plug-in Framework

**Estimated time to complete this lab: 40+ minutes**

Scenario
========

-   You have already developed the process to update the Loyalty Points based on
    the Loyalty Percentage in the Miles wise Tier Range form. Now there is a new
    formula for calculating the Loyalty Points, which is based on number of
    trips the customer has taken. It is not the right approach to change the
    code of the earlier business logic, as that logic may exist in a different
    package.

-   Plug-in framework enables your parameterized selection of a business rule to
    run the business logic for loyalty calculation.

-   You need to create a new field in the Accounts Receivable parameters screen,
    where you need to select the business rule you want to execute to calculate
    loyalty points. Plug-in framework will call the right business logic routine
    at runtime based on the selection in the parameter.

Exercise: Implement Plug-in Framework
=====================================

Task 1: Create new EDT MLALoyaltyCalcParameter
----------------------------------------------

1.  Open MyLabAirlines in Solution Explorer

2.  Right click on the project and click on **Add \> New Item**

3.  Select **EDT String** under **Dynamics 365 Items \> Data Types**

4.  Create a new EDT MLALoyaltyCalcParameter (Label: *Loyalty Calculation
    Parameter*)

Task 2: Table Extension: CustParameters
---------------------------------------

1.  Open MyLabAirlines in Solution Explorer

2.  In the Application Explorer, search for CustParameters table under Data
    Model

3.  Right click CustParameters and click on **Create Extension**

4.  A new element will be created in the Solution Explorer under *Table
    Extensions* folder named CustParameters.MyLabAirlines

5.  Add new field MLALoyaltyCalcParameter in CustParameters.MyLabAirlines by
    dragging the EDT MLALoyaltyCalcParameter and dropping on the Fields node of
    the extended table

6.  Add a new Field group: MLALoyaltyCalc

    1.  Label: *Loyalty Calculation Parameter*

    2.  Add field: MLALoyaltyCalcParameter

Task 3: Form Extension: CustParameters
--------------------------------------

1.  Save all.

2.  Open MyLabAirlines in Solution Explorer

3.  In the Application Explorer, search for CustParameters form under User
    Interface

4.  Right click CustParameters form and click on **Create Extension**

5.  A new element will be created in the Solution Explorer under *Form
    Extensions* folder named CustParameters.MyLabAirlines

6.  Open the form extension by double clicking it in the Solution Explorer.
    Restore the CustParameters datasource by right clicking on it and selecting
    that option, and find the new field group MLALoyaltyCalc

7.  Drag Field Group MLALoyaltyCalc and drop at the following location

    **Design \| Pattern \> Tab \> TabGeneral \> GeneralFastTab \>
    CustomerTabPage**

8.  Set the FrameType property of group MLALoyaltyCalc to *None*

Task 4: Create an abstract class MLALoyaltyCalcPlugIn
-----------------------------------------------------

1.  Open MyLabAirlines in Solution Explorer

2.  Right click on project and click on **Add \> New Item**

3.  Select Class under **Dynamics 365 Items \> Code**

4.  Create a new class MLALoyaltyCalcPlugIn with the following signature:

<pre><code>
[Microsoft.Dynamics.AX.Platform.Extensibility.ExportInterfaceAttribute()]
abstract class MLALoyaltyCalcPlugIn
{
}
</code></pre>


5.  Add the following two methods in the class

<pre><code>
public static MLALoyaltyCalcPlugIn getLoyaltyCalcParm(DDTCustFlyDetails _custFlyDetails)
{
    CustParameters custParameters = CustParameters::find();
    SysPluginMetadataCollection metadata = new SysPluginMetadataCollection();         
  
    metadata.SetManagedValue("LoyaltyCalcEngine", custParameters.MLALoyaltyCalcParameter);                 
    MLALoyaltyCalcPlugIn calc =  SysPluginFactory::Instance("Dynamics.AX.Application", classStr(MLALoyaltyCalcPlugIn), metadata);
        
    if (!calc)
    {
        warning("No calculation engine found");
    }
    return calc;
}
</code></pre>

<pre><code>
public abstract int calcLoyaltyPoints(DDTCustFlyDetails _custFlyDetails)
{     
}
</code></pre>


Task 5: Create Plug-in Clients
------------------------------

1.  Open MyLabAirlines in Solution Explorer

2.  Right click on project and click on **Add \> New Item**

3.  Select Class under **Dynamics 365 Items \> Code**

4.  Create a new class MLALoyaltyCalcPlugIn_Miles with the following signature;
    this extends the abstract class MLALoyaltyCalcPlugIn

<pre><code>
using System.ComponentModel.Composition;
 
[ExportMetadataAttribute("LoyaltyCalcEngine", "Miles")]
[ExportAttribute("Dynamics.AX.Application.MLALoyaltyCalcPlugIn")]

class MLALoyaltyCalcPlugIn_Miles extends MLALoyaltyCalcPlugIn
{
}
</code></pre>


5.  Business logic of the Loyalty Calculation should be written extending the
    method calcLoyaltyPoints() in this class, as follows:

<pre><code>
public int calcLoyaltyPoints(DDTCustFlyDetails _custFlyDetails)
    {
        int ret;
        ret = _custFlyDetails.FlyingMiles * (DDTTierRange::find(CustTable::find(_custFlyDetails.CustAccount).DDTCustomerTier).MLALoyaltyPercent/100);
        return ret;
    }
</code></pre>

6.  Similarly, create another Plug-in client considering number of trips as base
    for calculating loyalty points. Create a new class
    MLALoyaltyCalcPlugIn_Trips and add the following code:

<pre><code>
using System.ComponentModel.Composition;
 
[ExportMetadataAttribute("LoyaltyCalcEngine", "Trips")]
[ExportAttribute("Dynamics.AX.Application.MLALoyaltyCalcPlugIn")]

class MLALoyaltyCalcPlugIn_Trips extends MLALoyaltyCalcPlugIn
{
    public int calcLoyaltyPoints(DDTCustFlyDetails _custFlyDetails)
    {
        int ret;
        ret = DDTTierRange::find(CustTable::find(_custFlyDetails.CustAccount).DDTCustomerTier).MLALoyaltyPercent;
        return ret;
    }
}
</code></pre>


Task 6: Invoke Plug-in from class MLACustFlyDetailsEventHandler
---------------------------------------------------------------

1.  Open MyLabAirlines in Solution Explorer

2.  Find class MLACustFlyDetailsEventHandler, where we wrote code for Loyalty
    points calculation in an earlier lab. You need to comment out the old code
    by wrapping it with /\* and \*/ as follows:

<pre><code>
 /* custFlyDetails.MLALoyaltyPoints = custFlyDetails.FlyingMiles * (DDTTierRange::find(CustTable::find(custFlyDetails.CustAccount).DDTCustomerTier).MLALoyaltyPercent/100); */
</code></pre>


3.  Add new code to invoke the Plug-In framework, as follows:

<pre><code>
MLALoyaltyCalcPlugIn calc = MLALoyaltyCalcPlugIn::getLoyaltyCalcParm(custFlyDetails);
if(calc) custFlyDetails.MLALoyaltyPoints = calc.calcLoyaltyPoints(custFlyDetails);
</code></pre>


Check Output
============

1.  Build the project and check for errors.

2.  Navigate to **Accounts Receivable \> Setup \> Accounts Receivable
    Parameters**

3.  Under General tab, find Loyalty Calculation Parameters and type “Miles”

4.  Navigate to **Accounts Receivable \> Customers \> All Customers**

    1.  Open US-001

    2.  In the Flying Details fast tab enter a new record

    3.  You will find the Loyalty points calculation is based on the Flying
        Miles value

5.  Go back to the **General tab \> Loyalty Calculation Parameters amount** and
    change it to **Trips**

6.  Do the same operation and you will find the Loyalty calculation is based on
    count of trips
