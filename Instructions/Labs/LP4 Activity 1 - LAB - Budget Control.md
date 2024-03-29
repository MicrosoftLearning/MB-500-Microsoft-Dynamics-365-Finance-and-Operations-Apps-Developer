---
lab:
    title: 'Lab 1: Configure budget control'
    module: 'Learning Path 04: Manage budgeting'
---

# Configure budget control

Budget control supports the management of a company’s financial resources
through the chart of accounts, workflows, user groups, source documents and
journals, configurable calculation of available funds, budget cycles, and
thresholds. When controls are in place, an organization can plan, measure,
manage, and forecast its financial resources throughout its fiscal year.

In this lab, we will describe how to configure budget control.

The process of configuring budget control involves the following steps:

-   Define budget control parameters.

-   Define over budget permissions.

-   Define budget funds.

-   Define documents and business transactions that require budget checking.

-   Define budget models.

-   Define budget control rules.

-   Activate budget control.

Use the USMF company for the exercises in this lab. In this lab, all
configuration is discussed. Some of the setup is already present in the legal
entity USMF, and some setup is not. The purpose of this lab is to show you all
the settings necessary for budget control.

## Exercise 1 Budget control configuration

During this lab, you will configure budget control.

**Scenario**

Contoso, Ltd. has a controller who is responsible for budgets. Recently,
promotional expenses have increased. The controller must configure budget
control for main account promotional expenses to ensure that the budget for
promotional expenses is not exceeded this year.

### Define budget control parameters

1.  Navigate to **Budgeting** \> **Setup** \> **Budget control** \> **Budget
    control configuration.**

2.  Select the FastTab **Define parameters**, and then select **Create draft**
    in the action pane.
![Budget control configuration page with Create draft menu expanded. The FastTab Define parameters is selected.](../images/LP4P1.png)

1.  Verify the following settings:

-   **Account structure** value: **Manufacturing P&L**

-   **Budget control dimensions**: **Main account, Business unit**, and
    **Department**

-   **Budget control interval** field: **Fiscal year**

-   **Budget cycle time span** field: **Fiscal**

-   **Budget threshold** field: **90**

### Define over budget permissions

1.  Select FastTab **Over budget permissions** and select **Add** to add the
    user group **TestGroup1**. (If it is not possible to add a user group, make sure you selected **Create
    draft** in the previous step.)
![Budget control configuration page with the Create draft menu expanded. The FastTab Over budget permissions is selected.](../images/LP4P2.png)

### Define budget funds available

1.  Select FastTab **Budget funds available**.

2.  In the **Amounts to sum** section, verify that the fields **Original
    budget**, **Budget revisions**, and **Budget transfers** are selected.

3.  In the **Amounts to subtract** section, verify that the following fields are
    enabled:

    -   Actual expenditures

    -   Unposted actual expenditures

    -   Budget reservations for encumbrances

    -   Budget reservations for unconfirmed encumbrances

    -   Reduction to budget reservations for unconfirmed encumbrances

    -   Budget reservations for pre-encumbrances

    -   Budget reservations for unconfirmed pre-encumbrances
![Budget control configuration page with Create draft menu expanded. The FastTab Budget funds available is selected.](../images/LP4P3.png)

### Define documents and business transactions that require budget checking

1.  Select FastTab **Documents and journals**.

2.  Verify that the document journal **Vendor Invoice** is included in budget
    control.
![Budget control configuration page with the Create draft menu expanded. The FastTab Documents and journals is selected.](../images/LP4P4.png)

### Define budget models

1.  Select FastTab **Assign budget models**.

2.  Verify that **Budget cycle FY2024** is available.
![Budget control configuration page with Create draft menu expanded. The FastTab Assign budget models is selected.](../images/LP4P5.png)

### Define budget control rules

1.  Select FastTab **Define budget control rules**.

2.  Select **New** to create a new rule.

3.  Enter **Promo** in the **Budget control rule** field.

4.  Enter **Promotional expenses** in the **Description** field.

5.  Select **Add**.
![Budget control configuration page with the New menu expanded. The FastTab Define budget control rules is selected.](../images/LP4P6.png)

1.  Navigate to the **Criteria** section and select **Add new criteria.**

2.  Enter the following values:

    -   **Where** field: **MainAccount**

    -   **Operator** field: **is**

    -   **Value** field: **601600** (Main account number for Promotional
        expenses)

3.  Verify the following values:

    -   **Budget control interval**: **Fiscal year**

    -   **Budget cycle time span**: **Fiscal**

    -   **Budget threshold**: **90**
![Define budget control rules page with the fields Budget control rule, Description, Where, Operator, and Value filled in.](../images/LP4P7.png)

### Activate budget control

1.  Select the FastTab **Activate budget control**.

2.  Select **Activate** to activate the new budget control configuration.
![Budget control configuration page with the FastTab Activate budget control displayed. The Activate button is selected.](../images/LP4P8.png)

1.  Select **Activate** in the pop-up screen.
![Pop-up screen for activating the budget control configuration. The Activate button is activated.](../images/LP4P9.png)

1.  Verify that the budget control configuration is activated and the Budget
    control is turned on.
![Budget control configuration page with the FastTab Activate budget control displayed. Budget control configuration is activated.](../images/LP4P10.png)

1.  Close the form.

## Exercise 2 Create a budget register entry

1.  Navigate to **Budgeting** \> **Budget register entries**.

2.  Select **New** to create a new budget register entry.

3.  Select **FY2024** in the **Budget model** field.

4.  Select **Original budget** in the **Budget code** field.

5.  Navigate to the **Budget account entries** area.

6.  Select + **Add line** to create a new line.

7.  Select **1/1/2024** in the **Date** field.

8.  In the **Account structure** field, select **Manufacturing P**&**L**.

9.  In the **Dimension values** field, select **601600-001-022-008-Consume**.

10. Enter **10,000** in the **Amount** field.

11. Select **Save** in the action pane.

12. Select **Update budget balances** in the action pane.
![Budget register entries page with the menu update budget balances expanded.](../images/LP4P11.png)

13. Select **Update** in the pop-up screen.
![Pop-up screen for updating the budget entries. The Update button is activated.](../images/LP4P12.png)

14. The message **Operation completed** appears at top of the screen.
![The message Operation completed displayed at the top of the screen.](../images/LP4P13.png)

15. Close the form.

## Exercise 3 Create a vendor invoice journal

1.  Go to **Accounts payable** \> **Invoices** \> **Invoice journal**.

2.  Select **New** in the action pane.

3.  In the **Name** field, select **APInvoice**.

4.  Select **Lines** in the action pane.

5.  In the **Date** field, enter the date **1/1/2024**.

6.  In the **Account** field, select vendor **1001**.

7.  In the **Invoice date** field, enter the date **1/1/2024**.

8.  In the **Invoice** field, enter **1234**.

9.  In the **Description** field, enter **Promotional items**.

10. In the **Credit** field, enter **11,000**.

11. In the **Offset account** field, enter **601600-001---**.

12. Select **Post** in the action pane.
![Invoice journal lines page with the Post menu expanded.](../images/LP4P14.png)

13.  Check the messages at the top of the screen.

-   **Operation canceled**: Validating and posting journal

-   Transaction APIN000050 exceeds the budget funds available for dimension value 601600-001- by 11,000.00 USD.

14.  Check the Budget check results at the bottom of the screen.

-   Budget check failed (this may not immediately update)
![Invoice journal line page with the message that the budget is exceeding the available funds displayed.](../images/LP4P15.png)


