---
lab:
    title: 'Lab 1: Configure a prepayment invoice process'
    module: 'Learning Path 03: Implement and manage accounts payable and expenses'
---


# Lab 1 Configure a prepayment invoice process

Companies might issue prepayments (advance payments) to vendors for goods or
services before those goods or services are fulfilled. You can use two methods
to issue prepayments to vendors. One method creates a prepayment invoice that is
associated with a purchase order. The other method creates prepayment journal
vouchers by creating journal entries and marking them as prepayment journal
vouchers.

In this lab, the first method is described: the creation of a prepayment invoice
that is associated with a purchase order. You will define a prepayment value on
the purchase order, record and pay a prepayment invoice, and then apply
the prepayment invoice to the final invoice.

Use the USMF company for the exercises in this lab. In this lab, all
configuration is discussed; some setup is already present in legal entity USMF,
and some is not. The purpose of this lab is to show you all the settings
necessary for the prepayment invoice process.

## Exercise 1 Prerequisites prepayment invoice

In this exercise, you will check and configure the settings for the prepayment
invoice.

**Scenario**

Contoso, Ltd. has a purchase manager who must make prepayments for purchase
orders before the vendor will deliver items to Contoso, Ltd. The vendor requires
$25.00 USD prepayment. You will help the purchase manager set up the prepayment
invoice process.

### Inventory posting profile

1.  Navigate to the **Inventory management** module, select **Setup** \>
    **Posting** \> **Posting**.

2.  On the **Purchase order** tab, select **Prepayment**, and then verify that
    the main account is **132190** for all item codes.
![Inventory posting profile page with the FastTab purchase order expanded to enter the main account for prepayment.](../images/LP3P1.png)

1.  Close the form.

### Procurement category

1.  Navigate to the **Procurement and sourcing** module and select **Procurement
    categories**. A procurement category must be created to add a prepayment in
    the Purchase order.

2.  Select **Edit category hierarchy**.
![Procurement categories page with the menu Edit category hierarchy expanded to edit the procurement category.](../images/LP3P2.png)

1.  Select **New category node**.
![Procurement categories page with the menu New category node to create a Prepayment category node.](../images/LP3P3.png)

1.  Enter **Prepayment vendor** in the **Name** field.

2.  Enter **Prepayment** in the **Code** field.
![Procurement categories page with the menu Save to save the new Prepayment category node.](../images/LP3P4.png)

1.  Select **Save** and then close the form.

### Vendor posting profile

1.  Navigate to **Accounts payable** \> **Setup** \> **Vendor posting
    profiles**. Verify that a posting profile for prepayments was created.
![Vendor posting profile page with the Prepayment posting profile selected.](../images/LP3P5.png)

1.  Close the form.

### Accounts payable parameters

1.  Navigate to the **Accounts payable parameters** form, and then select
    **Ledger and sales tax**. In the **Posting profile for payment journal with
    prepayment** parameter field, select the **Prepayments posting** profile.

2.  Select **Notification** in the field **Prepayment application policy**. A
    visual indication that a prepayment invoice is available for application
    will display when the final invoice is created.
![Accounts payable parameters page, FastTab Ledger and sales tax expanded to fill in the Posting profile with prepayment fields.](../images/LP3P6.png)

1.  Select **Save**, then close the form.

## Exercise 2 Create a prepayment associated with a purchase order

In this exercise, you will create a prepayment invoice associated with a purchase
order.

1.  Navigate to **Accounts payable** \> **Purchase orders** \> **All purchase
    orders**, and then select purchase order **000039** from **Vendor 1001**.

2.  Select **Purchase** \> **Prepay** \> **Prepayment**.
![All purchase orders page displaying the Purchase tab with Prepayment selected to add a prepayment for an existing purchase order.](../images/LP3P7.png)

1.  Enter **Prepayment** in the **Description** field.

2.  Select the **Fixed** type.

3.  Enter **25** in the **Value** field.

4.  Go to the **Prepayment category ID** field and select the **Prepayment
    vendor** category you set up previously. Then select **OK**.
![Pop-up screen for creating the prepayment. The Save button is activated.](../images/LP3P8.png)

1.  Select **Save**.

2.  In the **Purchase** tab section, select **Actions** \> **Confirm** to
    confirm the purchase order.
![All purchase orders page with the Purchase tab displayed and Confirm selected to confirm the purchase order.](../images/LP3P9.png)

1.  The message **Operation completed** will appear on top of the screen.

## Exercise 3 Create a prepayment invoice

1.  Navigate to **Accounts payable \> Purchase orders \> All purchase orders**,
    and then select purchase order **000039** from **Vendor 1001**.

2.  On the **Invoice** tab, select **Generate** \> **Prepayment invoice**.
    This will open the vendor invoice form.
![All purchase orders page with the Invoice tab displayed. Prepayment invoice is selected to generate the prepayment invoice. ](../images/LP3P10.png)

3.  Enter **PRE001** in the **Number** field.

4.  Enter **Prepayment 001** in the **Invoice description** field.

5.  Select date **12/15/2023** in the **Invoice date** field.
![Prepayment invoices page with the fields Number, Invoice description, and Invoice date filled in.](../images/LP3P11.png)

1.  Select **Post** in the action pane to post the prepayment invoice.

2.  The message **The vendor invoice posting process is complete for vendor
    1001, invoice PRE001** will appear on top of the screen.

3.  Close the form.

4.  Navigate to **General ledger \> Periodic tasks** \> **Subledger journal
    entries not yet transferred**.

5.  Select the journal and then select **Transfer now** in the action pane. This
    step is necessary to perform the next exercise.
![Subledger journal entries page with Transfer now expanded.](../images/LP3P12.png)

1.  Close the form.

## Exercise 4 Pay the prepayment invoice

1.  Navigate to **Accounts payable \> Payments** \> **Vendor payment journal.**

2.  Select **New** to create a new Vendor payment journal.

3.  Select **VendPay** in the **Name** field.

4.  Select **Lines** in the action pane.

5.  Select vendor **1001 Acme Office Supplies** in the **Account** field and tab
    out.

6.  Select **Settle transactions**.

7.  Mark the prepayment invoice **PRE001** for settlement and select **OK**.
![Settle transactions page in the Vendor payment journal in which the prepayment line is marked.](../images/LP3P13.png)

1.  Select **Electronic** in the **Method of payment** field.

2.  Select **Post** in the action pane to post the payment.
![Vendor payment journal with the Post menu expanded.](../images/LP3P14.png)

1.  The message **Operation completed** will appear on top of the screen.

2.  Close the form.

## Exercise 5 Receive the items and post the invoice

1.  Navigate to **Accounts payable \> Purchase orders \> All purchase orders**,
    and then select purchase order **000039** from **Vendor 1001**.

2.  On the **Receive** tab, select **Generate** \> **Product receipt.**
![All purchase orders page with the Receive tab diplayed and the Product receipt menu expanded.](../images/LP3P15.png)

1.  Enter **1234** in the field **Product receipt** and select **OK.**
![Product receipt page with the Product receipt field filled in. The OK button is activated.](../images/LP3P16.png)

1.  The message **Operation completed** will appear on top of the screen.

2.  Close the form.

## Exercise 6 Post the invoice including the prepayment

1.  Navigate to **Accounts payable** \> **Purchase orders** \> **All purchase
    orders**, and then select purchase order **000039** from **Vendor 1001**.

2.  On the **Invoice** tab, select **Generate** \> **Invoice**.
![All purchase orders page with the Invoice tab displayed. The Invoice menu is expanded.](../images/LP3P17.png)

1.  Read the message **One or more pending invoices have unapplied paid
    prepayment invoices available to apply. Use the Apply Prepayment form to
    apply prepayment values to the selected invoice.**

2.  On the **Vendor Invoice** tab, select **Actions** \> **Apply
    prepayment.**
![Invoice page with the Apply prepayment menu expanded.](../images/LP3P18.png)

1.  Select the **Prepayment invoice** by marking the field, and then select
    **Apply prepayment** in the action pane.
![Apply prepayment page with the Apply prepayment menu expanded and the prepayment line selected.](../images/LP3P19.png)
The line of the prepayment is transferred to the invoice journal and will reduce
the total amount of the invoice with the amount we already paid.
![Invoice page with the applied prepayment.](../images/LP3P20.png)

1.  Enter **INV001** in the **Number** field.

2.  Enter **Invoice 001** in the **Invoice description** field, if you have it.

3.  Select date **12/15/2023** in the **invoice date** field.
![Prepayment invoices page with the fields Number, Invoice description, and Invoice date filled in.](../images/LP3P21.png)

1.  Select **Post** in the action pane. (Update match status if needed, then
    Post.)

    The message **The vendor invoice process is complete for vendor 1001,
    invoice INV001** will appear on top of the screen.

2.  **Close** the form.

3.  Navigate to **General ledger** \> **Periodic tasks** \> **Subledger journal
    entries not yet transferred**.

4.  Select the journal and select **Transfer now** in the action pane. Repeat
    this for the other two journals.
![Subledger journal entries page not yet transferred with the Transfer now menu expanded.](../images/LP3P22.png)

## Exercise 7 Check the balance of the invoice

1.  Navigate to **Accounts payable** \> **Vendors** \> **All vendors** and
    select Vendor **1001**.

2.  On the **Vendor** tab, select **Transactions** \> **Transactions**.

3.  Scroll all the way down to review the balance of the **INV001** invoice.

4.  Note the balance of the invoice, which is $1,975 USD (total invoice amount
    $2,000 USD minus the prepayment of $25.00 USD).
![All transactions page of Vendor displayed to check whether the prepayment has been deducted from the invoice.](../images/LP3P23.png)
