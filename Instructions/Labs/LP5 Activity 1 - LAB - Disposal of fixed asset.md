---
lab:
    title: 'Lab 1: Disposal of fixed assets'
    module: 'Learning Path 05: Manage fixed assets'
---

# Lab 1 Disposal of fixed assets

When an asset no longer has use to the company, because it is either being sold
or scrapped, the asset must be removed from the accounting books. Therefore, the
original acquisition price and accumulated depreciation of the asset are
reversed, and any surplus or loss from the disposal is posted to the profit and
loss statement.

On the Free text invoice page, you can process the sale of a fixed asset. A
fixed asset journal can be used for disposal -scrap of a fixed asset when there
is no customer for sale.

Use the USMF company for the exercises in this lab.

## Exercise 1 Fixed asset Disposal – Sale (Free text invoice)

### **Scenario**

Contoso, Ltd. has a new finance manager who wants to sell two fixed assets. One
is sold to a customer, and the other fixed asset has no customer to sell the
asset to. The finance manager will use the Scrap/Sale journal for the disposal
of the fixed asset with no customer.

1.  Navigate to **Accounts receivable** \> **Invoices** \> **All free text
    invoices**.

2.  Select **New**.
![Free text invoice page with the New menu expanded to create a free text invoice.](../images/LP5P1.png)

1.  In the **Customer account** field, enter **US-021**.

2.  In the **Main account** field in the **Invoice lines** FastTab, enter the
    main account number **801100**.

3.  In the **Unit price** field, enter **300.00** USD.
![Free text invoice page with the Free text invoice header expanded to add Customer account.](../images/LP5P2.png)

1.  Navigate to the FastTab **Line details**.

2.  In the **Fixed asset number** field, enter **COMP-000002**.
![Free text invoice page with the Free text invoice lines expanded to add Main account.](../images/LP5P3.png)

1.  Select **Post** in the action pane.

2.  Select **OK** in the pop-up screen.
![Pop-up screen to post the free text invoice. The OK button is activated.](../images/LP5P4.png)

1.  The message **Operation completed** appears at the top of the screen.
![Operation completed message that appears at the top of the screen.](../images/LP5P5.png)

1.  Close the page.

2.  Navigate to **Fixed assets** \> **Fixed assets** \> **Fixed assets sold or
    scrapped**.

3.  Select **Books** in the action pane.
![Fixed assets page with menu item Books expanded to check the status of the fixed assets.](../images/LP5P6.png)

1.  The status of the fixed assets is **Sold**, and on the FastTab
    **Purchase/Sale**, the reference to the free text invoice is shown.

2.  Close the form.

## Exercise 2 Fixed asset Disposal – Scrap (Journal Scrap/Sale)

1.  Go to **Fixed assets** \> **Journal entries** \> **Fixed assets journal**.

2.  Click New.

3.  Select **FACur** in the name field.

4.  Select **lines**.
![Journal entry page for fixed asset journal is expanded to create a new journal line.](../images/LP5P7.png)

1.  Select **Disposal – Scrap** in the **Transaction type** field.

2.  Select **COMP-000006** in the **Account** field.

	-   The book **SLSL** is automatically selected.
	-   Do not enter any value in the Debit/Credit column.
![Fixed assets journal line entry is expanded to create a new journal line of type Disposal - Scrap.](../images/LP5P8.png)

1.  Select **Post** in the action pane.

2.  Select **OK** in the pop-up screen if you get one.
![Pop-up screen to post the free text invoice. The OK button is activated.](../images/LP5P9.png)

1.  The error **Posting results for journal batch number 00630 Voucher
    FACRxxxxxx Disposal parameters/Post value Net book value does not exist**
    appears at the top of the page. We’ll discuss this further, and address it,
    in the next exercise.
![Error message that appears because the net book value is not configured for disposal - scrap.](../images/LP5P10.png)

1.  Close the page.

## Exercise 3 Configuration posting profile Disposal - scrap

1.  Navigate to **Fixed assets** \> **Setup** \> **Fixed assets posting
    profile**.

2.  Select the FastTab **Disposal**.

3.  Select **Scrap**.
![Fixed assets posting profiles page with Disposal - Scrap expanded to configure posting profile net book value.](../images/LP5P11.png)

	- The posting profile is not configured for scrap. This is the reason the
following error message appears: **Posting results for journal batch number
00630 Voucher FACRxxxxxx Disposal parameters/Post value Net book value does
not exist.**

1.  Select **Add**.

2.  Enter the following information:

    -   Enter the value **SLSL** in the **Book** field.

    -   Select **Net book value** in the **Post value** column.

    -   Select Main account **801100**.

    -   Select Offset account **801100**.

    -   Select **Add**.

    -   Enter the value **T_150_SLLR** in the **Book** field.

    -   Select **Net book value** in the **Post value** column.

    -   Select Main account **801100**.

    -   Select Offset account **801100**.
![Fixed assets posting profiles page with Disposal - Scrap expanded to configure posting profile net book value.](../images/LP5P12.png)

1.  Navigate to **Fixed assets** \> **Journal entries** \> **Fixed assets
    journal**.

2.  Select the journal entry for the disposal – scrap of the fixed asset
    **COMP-000006**.

3.  Select **Post** in the action pane.

	- The message **Operation completed** appears at the top of the screen.
![Operation completed message that appears at the top of the screen.](../images/LP5P13.png)

1.  Close the page.

2.  Navigate to **Fixed assets** \> **Fixed assets** \> **Fixed assets sold or
    scrapped**, and select (any of) the asset COMP-000006

3.  Select **Books** in the action pane.
![Fixed asset page with menu item Books expanded to check the status of the fixed assets. ](../images/LP5P14.png)

	- The status of the fixed assets is **Scrapped**.

1.  Close the form.

## Exercise 4 Generate the Fixed asset disposals report 

1.  Navigate to **Fixed assets** \> **Inquiries and reports \> Transaction
    Reports** \> **Fixed asset disposals.**

2.  On the FastTab **Records to include** select **Filter**.

3.  Enter value **SLSL** in the **Book** field Criteria.

4.  Select **OK,** and **OK.**
![Pop-up screen that appears for generating the report Fixed asset disposals. The OK button is activated.](../images/LP5P15.png)

The report will be generated.
![Output of the Fixed asset disposals report.](../images/LP5P16.png)

The field status shows how the fixed asset was disposed.
