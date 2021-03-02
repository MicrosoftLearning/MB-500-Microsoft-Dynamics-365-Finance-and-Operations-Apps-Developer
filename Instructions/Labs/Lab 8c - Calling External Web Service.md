---
lab:
    title: 'Exercise 03: Calling external web services'
    module: 'Module 08: Integration'
---

**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**

**Lab 8c - Calling External Web Services**

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

    -   Lab 1 – Development Environment Configuration completed

Lab Overview
============

-   Dependency: Lab 1 – Development Environment Configuration should be
    completed

-   Calling an external Web Service from Dynamics 365 Finance and Operations
    apps

**Estimated time to complete this lab: 30+ minutes**

Scenario
========

-   In this lab we are trying to access an external Web Service from Dynamics
    365 Finance and Operations apps.

-   To achieve that we will be creating a wrapper class using C\# that will read
    the Web Service through Service Reference. The dll of this wrapper class
    will be added as a reference to the Dynamics 365 Finance and Operations
    project. A runnable class will be created in Dynamics 365 Finance and
    Operations apps to call the referenced dll and throw an info() message. For
    this exercise, we will use a third-party web service which is freely
    available.

Exercise: Calling an External Web Service 
==========================================

Task 1: Creating the C\# Wrapper class
--------------------------------------

1.  Open Visual Studio and close the Existing Solution by selecting **File \>
    Close Solution**

2.  Select **File \> New Project**

3.  Select template **Class Library** under **Visual C\#**

4.  Type project name GoldRateProvider

5.  Save the project in a new Solution GoldRateService

6.  Right click **References** and select **Add Service Reference**

7.  Type <http://www.freewebservicesx.com/GetGoldPrice.asmx?WSDL> as address and
    select **Go**

8.  Once it resolves, add GetGoldPriceSoap as NameSpace GoldServiceRef and
    select **OK**

9.  Add a new C\# class GoldData.cs

10. Its code should be:

<pre><code>using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using GoldRateProvider.GoldServiceRef;
using System.ServiceModel;

namespace GoldRateProvider
{
    public class GoldData
    {
        public static ArrayOfString getRate()
        {
            var binding = new System.ServiceModel.BasicHttpBinding();
            var endpointAddress = new EndpointAddress("http://www.freewebservicesx.com/GetGoldPrice.asmx");
            GetGoldPriceSoapClient client = new GetGoldPriceSoapClient(binding, endpointAddress);

            return client.GetCurrentGoldPrice("domaindynamicstravel@gmail.com", "pass@word");
        }
    }
}
</code></pre>

11. **Save** and **Build** the Project GoldDataProvider

Task 2: Creating the D365 for Fin & Ops class
---------------------------------------------

1.  In the Solution Explorer GoldRateService, right click and add a **new
    Project**

2.  Select **Dynamics 365 \> Finance Operations**

3.  Write project name: GoldRate

4.  Right click on **References** in the GoldRate project and select **Add
    Reference**

5.  Click on **browse** and select

    **Documents \> Visual Studio 2015 \> Projects \> GoldRateService \>
    GoldRateProvider \> Bin \> Debug \> GoldDataProvider.dll**

6.  In the Solution Explorer GoldRate project, right click and **Add \> New
    Item**

7.  Under **Dynamics 365 Items**, Click **Code** and create a new Runnable Class
    DDTGetGoldRate

8.  Within the main method, add the following code:

<pre><code>System.String[] goldRate = GoldRateProvider.GoldData::getRate().ToArray();
info(goldRate.GetValue(0));
</code></pre>

9.  Right click the project name in Solution Explorer and select **Set as
    Startup Object**

10. Right click the class name in Solution Explorer and select **Set as Startup
    Object**

11. **Save** and **Build** the solution and click on **Start**

Check Output
============

Execute the Runnable class DDTGetGoldRate from Visual Studio. An info() message
should pop up with the rate for gold that is coming from the Web Service.
