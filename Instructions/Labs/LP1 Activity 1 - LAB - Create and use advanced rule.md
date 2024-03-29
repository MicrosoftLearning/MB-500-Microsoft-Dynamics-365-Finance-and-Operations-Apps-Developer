---
lab:
    title: 'Lab 1: Configure an advanced rule'
    module: 'Learning Path 01: Set up and configure financial management; work with General Ledger'
---


# Lab 1 Configure an advanced rule

Advanced rules link a financial dimension or multiple financial dimensions to a
main account or a range of main accounts. The advanced rule enables additional
information to be gathered for reporting and analysis beyond what you have set
up in related account structures.

If we add a dimension to main accounts in an account structure, that dimension
will be available for all the main accounts in that specific account structure.
Advanced rules can help you manage exceptional conditions by configuring an
additional dimension to a main account or even a subset of main accounts in the
same account structure.

For example, you agree on a relocation expense budget per employee. To monitor
these budgets, you want to be able to report the relocation expenses per
employee for only one specific main account in an existing account structure.

Use the USMF company for the exercises in this lab.

In this lab, you will configure an advanced rule structure.

## Exercise 1 Create an advanced rule structure 

**Scenario**

Contoso, Ltd. has a new HR manager who plans to create a Relocation expenses per
worker report. You need to set up the advanced rule structure with an extra
dimension *Worker* for the main account *602210 Employee Relocation Expense.*

1.  Navigate to the **General ledger** module, and then select **Chart of
    Accounts** \> **Structures** \> **Advanced rule structures.**

2.  Select the **New** button to create an advanced rule structure.
![Advanced rule structures page with the New menu expanded to create an advanced rule structure](../images/LP1P1.png)
3. Enter **Relocation expenses** in the **Advanced rule structure** field.

4. Enter **Relocation expenses** in the **Description** field and select **OK**.
![Create advanced rule structure menu with the Advanced rule structure and Description fields filled in. The OK button is activated.](../images/LP1P2.png)

5. Select **Add segment**.
![Relocation expenses view of Advanced rule structures with focus on Add segment.](../images/LP1P3.png)

6. Select **Worker** and select **Add segment**.
![Relocation expenses view with an overview of all available segments in the Add segment pane. Focus is on the Worker segment and the Add segment button.](../images/LP1P4.png)

7. Leave the asterisk in the **Worker** field to ensure that Worker is a
    mandatory field.
![Relocation expenses view of the Advanced rule structures tab with segment worker active for all values.](../images/LP1P5.png)

8. Select **Activate** in the action pane.
![Training and development view of the Advanced rule structures tab. Focus is on the Activate button.](../images/LP1P6.png)

9. Select **Activate** in the pop-up screen.
![Pop-up screen for activating the advanced rule structure. Focus is on the Activate button.](../images/LP1P7.png)

10.Close the form.

## Exercise 2 Add the advanced rule to an account structure 

In this exercise, you will add the advanced rule structure to an existing
account structure. Main account **602210 Employee Relocation Expense** is
configured in account structure **Manufacturing P&L**.

1.  Navigate to the **General ledger** module, and then select **Chart of
    accounts** \> **Structures** \> **Configure account structures.**

2.  Select **Manufacturing P&L.**
![Account structures Standard view with focus on the account structure Manufacturing P&L.](../images/LP1P8.png)

3. Select **Edit** in the action pane.
![Manufacturing P&L account structure on the Account structures tab. The Edit button is expanded to adjust the Manufacturing P&L account structure.](../images/LP1P9.png)

4. Select **Advanced rules** in the action pane to configure the advanced rule.
![Account structure Manufacturing P&L. The Advanced rules button is selected to attach the advanced rule to the account structure Manufacturing P&L.](../images/LP1P10.png)

5. Select + **New** in the action pane**.**
![Advanced rule structures page with the New menu expanded to attach an advanced rule structure to account structure Manufacturing P&L.](../images/LP1P11.png)

6. Select **Yes** in the pop-up screen if you get one. (By default, No is
    activated
![Pop-up screen for creation of an advanced rule. The No button is activated. ](../images/LP1P12.png)

7. Enter **Relocation Expenses** in the **Advanced rule** field.

8. Enter **Relocation Expenses** in the **Name** field and select **Create**.
![Create an advanced rule menu with the Advanced rule structure and name fields filled in. The Create button is activated.](../images/LP1P13.png)

9. Select + **Add new criteria**.
![Advanced rules page with the New button activated to add new criteria.](../images/LP1P14.png)

10. Enter **602210** in the **Value** field for MainAccount.
![Advanced rules page with advanced rule criteria expanded. The fields Where, Operator, and Value are filled in.](../images/LP1P15.png)

11. Navigate to **Advanced rule structures**, and then select **Add** \>
    **Relocation expenses** \> **Add** to add a structure.
![Create advanced rule structure menu with Add advanced rule structure to advanced rule expanded. The fields Name, Description, and Segments are filled in. Focus is on the Relocation expenses advanced rule and the Add button.](../images/LP1P16.png)

12. Close the form.

13. **Activate** the account structure in the action pane.

14. Select **Activate** in the pop-up screen.

15. Close the form.

## Exercise 3 Create a journal entry with the new advanced rule

1.  Navigate to **General ledger** \> **Journal entries** \> **General
    journals**.

2.  Select **New** to create a new journal.

3.  Select **GenJrn** in the **Name** column.

4.  Select the **Lines** button in the action pane.
![The general journal menu with the WF General Journal name field filled in. Focus is on the Lines button.](../images/LP1P17.png)

5. Enter **12/14/2023** in the **Date** field.
![A screenshot of a computer Description automatically generated](../images/LP1P18.png)

6. Enter in the Account field Main account 602210, value 001 for dimension
    Business Unit, value 022 for dimension Department, value 007 for dimension
    Cost Center, value Audio for dimension Item group and value **000001 for
    dimension worker.**
![Account structure selection](../images/LP1P19.png)
   A value is **mandatory** for the dimension worker you set up in the advanced rule structure. If you do not select a value, the following message appears: **Blank is not allowed for Worker for the combination**.
![Journal voucher page displaying the message Blank is not allowed for Worker for the combination.](../images/LP1P20.png)

7. Enter **$2,000.00** in the **Debit** field.

8. Select main account **602200** in the **Offset** account.

    The dimension values will be copied from the main account 602210 except the
    value 000001 for worker. The dimension worker is configured for only main
    account 602200 by using an advanced rule.
![The general journal lines menu with the Account field filled in, including all the dimensions.](../images/LP1P21.png)



9. Select **Post** in the action pane to post the journal.

10. Select **Voucher** to verify if the value **000001** for worker was posted
    for main account 602210 Employee Relocation Expense. *Voucher is only
    available if you posted the journal.*
![The general journal lines menu with focus on the field voucher.](../images/LP1P22.png)
![Account number selection](../images/LP1P23.png)

11. Close the form.
