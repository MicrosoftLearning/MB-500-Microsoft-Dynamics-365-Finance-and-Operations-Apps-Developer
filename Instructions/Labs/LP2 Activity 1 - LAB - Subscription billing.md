---
lab:
    title: 'Lab 1: Set up recurring contract billing parameters'
    module: 'Learning Path 02: Implement accounts receivable, credit, collections, and revenue recognition'
---


# Lab 1 Set up recurring contract billing parameters

A subscription billing solution enables companies to manage contract revenue
opportunities and recurring billing through billing schedules.

The solution has three modules that can be used independently or used together.

-   **Recurring contract billing** enables recurring billing and price
    management to provide control over pricing and billing parameters, contract
    renewal, and consolidated invoicing.

-   **Revenue and expense deferrals** eliminate manual processes and dependency
    on external systems by managing revenue and enabling real-time insight into
    monthly recurring revenue.

-   **Multiple element revenue allocation** helps with revenue compliance by
    handling pricing and revenue allocation across multiple items.

In this lab, you will set up recurring contract billing and create an invoice by
using the recurring contract billing module. Use the USMF company for the
exercises in this lab.

## Exercise 1 Set up a Billing schedule group


Use the Recurring contract billing parameters to set up the default values for
billing schedules created in the recurring contract billing module.

**Scenario**

The finance manager of Contoso, Ltd. defines a monthly billing schedule to
manage subscription revenue opportunities. The manager also wants to learn how
to update prices in a single action. You need to help the finance manager set up
the recurring contract billing and create recurring invoices for installation
services.

1.  Navigate to the **subscription billing** module, and then select **Recurring
    contract billing \> Setup \> Billing schedule group**.

2.  Select the **New** button to create a new billing schedule group.

3.  In the **Billing schedule group** field, enter **Service**.

4.  In the **Description** field, enter **Installation service**.

5.  In the **Billing frequency** field, enter **Monthly**.

6.  In the **Billing interval** field, enter **1**.

7.  In the **Pricing method** field, select **Standard**. Standard pricing is
    used from the released product.

8.  In the **Item type** field, select **Standard**.

9.  Set **Invoice separately** to **Yes.**

10. Set **Renew automatically** to **No**.

11. Set **Escalation** to **Yes**.
![Billing schedule group page with the fields Billing schedule group, Description, Billing frequency, Billing interval, Pricing method, and Item type filled in.](../images/LP2P1.png)

1.  Select **Save**, and then close the form.

## Exercise 2 Create a billing schedule

1.  Navigate to the **subscription billing** module, and then select **Recurring
    contract billing** \> **Billing schedules** \> **All billing schedules**.

2.  Select the **New** button to create a new billing schedule.

3.  In the **Billing schedule group**, select **Service**.

4.  In the **Customer account** field, select customer **US-002**.

5.  In the **Billing start date** field, enter **1/1/2023**.

6.  In the **Number of periods** field, enter **12**. The **Billing end date**
    field is updated based on the number of periods you enter.

7.  Select **OK**.
![Create billing schedule page with the New menu expanded to create a new billing schedule. The OK button is activated.](../images/LP2P2.png)

1.  Navigate to the **Billing schedule lines** FastTab.
![Create billing schedule page with the FastTab Billing schedule lines expanded to create a new billing schedule line.](../images/LP2P3.png)

1.  Select **Add line** to add a line to the billing schedule.

2.  In the **Item number** field, select item **S0001**.

3.  Select **View billing detail**.
![Billing schedule page with the FastTab Billing schedule lines activated.](../images/LP2P4.png)

1.  **View** the billing details.
![Billing schedule page with View billing details expanded to view the billing details.](../images/LP2P5.png)

1.  Select **Save**, close the form, and then close the next form.

## Exercise 3 Generate invoice for billing schedule


1.  Navigate to the **Subscription billing** module, and then select **Recurring
    contract billing** \> **Billing schedules** \> **All billing schedules.**

2.  Select the billing schedule **USMF-000000001** you created in exercise 2.

3.  Navigate to the **Invoice** section and select **Generate invoice** without
    selecting the link.

4.  Enter **1/1/2023** in the **From date** field.

5.  Enter **1/31/2023** in the **To date** field.

6.  On the **Invoice processing** FastTab, select **Post invoice automatically**
    for Posting option. The sales order will be created, and the invoice will be
    posted automatically.

7.  Enter **1/31/2023** in the **Invoice date** field.

8.  Select **View billing schedules** to review the billing schedule lines that
    are available to bill a customer.
![Create billing schedule page with the tab Generate invoice expanded to generate an invoice. The view billing schedules button is activated.](../images/LP2P6.png)

1.  Select **Generate all**.
![Create billing schedule page with the tab Generate invoice expanded to generate an invoice. The generate all button is activated.](../images/LP2P7.png)
The message **1 sales order (**number**) has been created for 1 line** appears.

1.  Close the form.

## Exercise 4 Review billing schedule

1.  Navigate to the **Subscription billing** module, and then select **Recurring
    contract billing** \> **Billing schedules** \> **All billing schedules.**

2.  Select the billing schedule **USMF-000000001** you created in exercise 2.

3.  Navigate to the **Billing schedule lines** FastTab.
![Create billing schedule page with the FastTab Billing schedule lines expanded to view the billing details.](../images/LP2P8.png)

1.  Select **View billing detail**.
![Billing schedule page with the FastTab Billing schedule lines expanded to view the billing details.](../images/LP2P9.png)

1.  Review the schedule and note the status of the billing line, the sales order
    number, the invoice number, and the invoice date.
![Billing schedule page with the menu view billing details expanded to view the billing details.](../images/LP2P10.png)

1.  **Close** the form.

## Exercise 5 Update price of an item 

When the standard pricing method is used in a Billing Schedule group, you should
set up the unit price for a billing schedule line item in the Production
information management module.

1.  Navigate to **Product information management \> Products \> Released
    products** and select **item S0001.**

2.  Select the **Sell** tab and navigate to **Trade agreements \> View trade
    agreements**.
![Sell FastTab on the Released products menu is selected to view trade agreements. The Edit selected lines button is selected.](../images/LP2P11.png)

1.  Select **Edit selected lines.**

2.  Select **S_Price** in the **Name** field and select **OK**.
![Sell FastTab on the Released products menu is selected to edit a trade agreement. OK is activated.](../images/LP2P12.png)

1.  Select **Edit**.

2.  Select the **Details** FastTab and enter the date **12/31/2022** in the **To
    date** field.
![Page Journal lines on the Trade agreements menu is selected to edit a trade agreement.](../images/LP2P13png)

1.  Select **Post** and **OK.** Select the trade agreement again**,** and **Edit
    selected lines,** and **OK.**

2.  Select the **New** button to create a new Trade agreement.

3.  Select **S0001** in the **Item relation** field.

4.  Enter **1** in the **From** field.

5.  Enter **275**.**00** in the **Amount** field.

6.  Enter the value **1/1/2023** in the **From date** field on the **Details**
    FastTab.
![Page Journal lines on the Trade agreements menu is selected to edit a trade agreement. The fields Item number, From, Amount, Currency, and From date are filled in.](../images/LP2P14.png)

1.  Select **Post** to post the new Trade agreement, and **OK**.

2.  Note the message **Operation completed**, and then close the form.

## Exercise 6 Update price of billing schedule item lines


1.  Navigate to the **subscription billing** module, and then select **Recurring
    contract billing** \> **Periodic tasks** \> **Price update**.

2.  Set **Pricing method** to **Standard**.

3.  Navigate to the **Records to include** FastTab.

4.  Select **Filter.**

5.  Enter the criteria **USMF-000000001** in the **Billing schedule number**
    field.

6.  Select **OK.**
![The price update in the periodic tasks is selected. OK is activated for the price update.](../images/LP2P15.png)

1.  Select **View preview**.
![The View preview on the Price update page is expanded. The View preview button is activated.](../images/LP2P16.png)

1.  Select the line and select **Process**.
![The view preview update is displayed. The Process button is activated.](../images/LP2P17.png)

1.  Note the message in the Action center.
![The message billing schedule lines have been updated is shown.](../images/LP2P18.png)



## Exercise 7 Review the updated prices of billing schedule item lines

1.  Navigate to the **subscription billing** module, and then select **Recurring
    contract billing** \> **Billing schedules** \> **All billing schedules**.

2.  Select the billing schedule **USMF-000000001** you created in exercise 2 by
    selecting the link.

3.  Navigate to the **Billing schedule lines** FastTab.
![Billing schedule page with the Billing schedule lines FastTab expanded to view the billing details.](../images/LP2P19.png)

1.  Select **View billing detail**.
![Billing schedule page with the Billing schedule lines FastTab expanded to view the billing details.](../images/LP2P20.png)

1.  Review the schedule and note the new updated prices of billing schedule item
    lines.
![Billing schedule page with the View billing details menu expanded to view the billing details.](../images/LP2P21.png)

1.  Close the form.
