---
lab:
    title: 'Lab 2: Create a new EDT table and form'
    module: 'Learning Path 02: Build finance and operations apps'
---

**MB-500: Microsoft Dynamics 365: Finance and Operations Apps Developer**


Change Record
=============

<html>
<table><tr><th>Version</th><th>Date</th><th>Change</th></tr>
<tr><td>1.0</td><td>29 Sep 2023</td><td>Initial release</td></tr>
</table>
</html>


# Objective

This lab consists of several exercises.

The first exercise is basic **setup** in Visual Studio in order to prepare to
code.

From exercise 2 to 4, we will create an interface in the Human Resource module
to enter exam details. To create this interface, you need to create a few data
types, data model and user interfaces, which are covered in exercise 2, 3 and 4
respectively.

# Exercise 1: Create model and project 

1.  Select Visual Studio 2019 from the desktop.

2.  Select **Continue without code** in the popped-up dialog **Visual Studio
    2019.**
![Visual Studio 2019 popup](images/13095be3f3840a246efeb88b75746fbf.png)
<br>**Note:** *You can check if there is already a model created named **MB500Model**. If not, please continue from step 7 up to step 12. If the model is already present, execute step 3 to step 6.*


1.  Open **Solution Explorer**.

2.  Right click on the solution *SlnMb500Lab*.

3.  Select **Add \> New project**.

4.  Type *PrjMb500Lab-2* as the name of the new project.

5.  Select **Extensions \> Dynamics 365 \> Model management \> Create model**
    and enter the following information to create a new model, then select
    **Next**:

    -   **Model name**: MB500Model

    -   **Model publisher**: Microsoft training

    -   **Layer**: usr

    -   **Version**: 1.0.0.0

    -   **Model display name**: MB-500 lab exercise

        ![Create model, Add parameters](images/cb12440fc812c4253518ab527ea05304.png)

6.  Select **Create new package** followed by the **Next** button.

    ![Create model, Select package](images/ccf3ecd7b8a254d20321b28e88001460.png)

7.  Select the following referenced packages followed by the **Next** button:

    -   ApplicationFoundation

    -   ApplicationPlatform

    -   PersonnelManagement

8.  In the **Summary** step, check **Create new project** and select the
    **Next** button.

9.  In the **Configure your new project** dialog, enter *PrjMb500Lab-2* and
    *SlnMb500Lab* in the **Project name** and **Solution name** fields
    respectively, then select **Create**.

    -   Also: Select Tools \> Options \> Dynamics 365 \> Projects \> and check
        the boxes to Organize projects by element type and Synchronize database
        on build for newly created project

10. The new solution and project will appear in **Solution Explorer**.

# Exercise 2: Create new data types

## Task 1: Create a new extended data type - MBExamID

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Add** \> **New Item.**

3.  Under **Dynamics 365 Items**, select **Data Types** and select **EDT
    String**.

4.  In the **Name** field type *MBExamID* and select the **Add** button.

5.  A new folder **EDT Strings** will be created in the **Solution Explorer**
    under the project *PrjMB500Lab-2*.

6.  In the **EDT Strings** folder, a new element *MBExamID* will also be
    created.

7.  Open the *MBExamID* in the **Element designer** pane and right click on it
    to select the **Properties** option.

8.  Type *Exam ID* in the **Label** property

**Note:** *Ideally, the labels should be added in the label file for best practice, as practiced in Lab 1.*


## Task 2: Create a new extended data type - MBExamName

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Add** \> **New Item.**

3.  Under **Dynamics 365 Items**, select **Data Types** and select **EDT
    String**.

4.  In the **Name** field type *MBExamName* and select the **Add** button.

5.  In the **EDT Strings** folder, a new element *MBExamName* will also be
    created.

6.  Open the *MBExamName* in the **Element designer** pane and right click on it
    to select the **Properties** option.

7.  Type *Exam Name* in the **Label** property

**Note:** *Ideally, the labels should be added in the label file for best practice, as practiced in Lab 1.*


## Task 3: Create a new extended data type - MBExamDate

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Add** \> **New Item.**

3.  Under **Dynamics 365 Items**, select **Data Types** and select **EDT Date**.

4.  In the **Name** field type *MBExamDate* and select the **Add** button.

5.  A new folder **EDT Dates** will be created in the **Solution Explorer**
    under the project *PrjMB500Lab-2*.

6.  In the **EDT Dates** folder, a new element *MBExamDate* will also be
    created.

7.  Open the *MBExamDate* in the **Element designer** pane and right click on it
    to select the **Properties** option.

8.  Type *Exam Date* in the **Label** property

**Note:** *Ideally, the labels should be added in the label file for best practice, as practiced in Lab 1.*

## Task 4: Create a new base enum - MBExamOrganizer

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Add** \> **New Item.**

3.  Under **Dynamics 365 Items**, select **Data Types** and select **Base
    Enum**.

4.  In the **Name** field type *MBExamOrganizer* and select the **Add** button.

5.  A new folder **Base Enums** will be created in the **Solution Explorer**
    under the project *PrjMB500Lab-2*.

6.  In the **Base Enums** folder, a new element *MBExamOrganizer* will also be
    created.

7.  Open the *MBExamOrganizer* in the **Element designer** pane and right click
    on it to select the **Properties** option.

8.  Type *Organizer* in the **Label** property.
<br><br>**Note:** *Ideally, the labels should be added in the label file for best practice, as practiced in Lab 1.*

9.  Right click on *MBExamOrganizer* and select **New Element**.

10. Create two **Base Enum elements**: *Internal* and *External*.

11. Use the same **Labels** in the **Enum Element** properties.

# Exercise 3: Create new Data models

## Task 1: Create a new Table - MBExamTable

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Add** \> **New Item.**

3.  Under **Dynamics 365 Items**, select **Data Model** and select **Table**.

4.  In the **Name** field type *MBExamTable* and select the **Add** button.

5.  A new folder **Tables** will be created in the **Solution Explorer** under
    the project *PrjMB500Lab-2*.

6.  In the **Tables** folder, a new element *MBExamTable* will also be created.

7.  Open the *MBExamTable* in the **Element designer** pane.

8.  Select the three extended data types from the **Solution Explorer** and drop
    them at the **Fields** node of *MBExamTable*: *MBExamID*, *MBExamName* and
    *MBExamDate*.

9.  Select the base enum from the **Solution Explorer** and drop it on the
    **Fields** node of *MBExamTable*: *MBExamOrganizer*.

10. Remove the *MB* prefix from all the field names. Hence, the field names will
    become: *ExamID*, *ExamName*, *ExamDate* and *ExamOrganizer*.

11. Navigate to the **Field groups** node of the table *MBExamTable* and add a
    new Field group *MBExam*. In the **Label** property of the field group type
    *Exam details*.

12. Add all the four fields into the newly created **Field group** by dragging
    them from the **Fields** node and dropping on the *MBExam* field group.

13. In the **Indexes** node, create a new index *ExamIdx*.

14. Change the **Allow Duplicates** property of the *ExamIdx* index to *No*.
<br><br>**Note:** *This will make the index unique.*

15. Add the *ExamID* field in the newly created index by dragging the field from
    the **Fields** node and dropping on the *ExamIdx* index.

# Exercise 4: Create new User interfaces

## Task 1: Create a new Form – MBExamTable

1.  **Save all**, and right click the project and select **Build**. This will
    also perform a sync.

2.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

3.  Select **Add** \> **New Item.**

4.  Under **Dynamics 365 Items**, select **User Interface** and select **Form**.

5.  In the **Name** field type *MBExamTable* and select the **Add** button.

6.  A new folder **Forms** will be created in the **Solution Explorer** under
    the project *PrjMB500Lab-2*.

7.  In the **Forms** folder, a new element *MBExamTable* will also be created.

8.  Open the *MBExamTable* form in the **Element designer** pane.

9.  Add table *MBExamTable* in the **Data Sources** node of the *MBExamTable*
    form by dragging the table from the **Solution Explorer** and dropping onto
    the **Data Sources** node.

10. Right click on the **Design** node and select **Simple List** as the
    **Pattern**.

11. Type the following properties of the **Design** node:

    1.  **Caption**: *Exam Details*

    2.  **Data Source**: *MBExamTable*

12. Right click on the **Design** node and add three controls by selecting New.

    1.  **Action Pane**

    2.  **Group**

    3.  **Grid**

13. Rename the newly created **Action Pane** control to *ActionPane*.

14. Rename the newly created **Group** control to *FilterGroup*.

15. Add sub-pattern **Custom and Quick Filters** by right clicking on
    *FilterGroup*.

16. Add the **QuickFilter** control under *FilterGroup* by right clicking on
    *FilterGroup* and selecting **New**.

17. Rename the newly created **QuickFilter** control to *QuickFilter*.

18. Rename the newly created **Grid** control to *Grid*.

19. Navigate to the **Data Source** property of the **Grid** and select
    *MBExamTable*

20. Navigate to the **Field groups** node under the *MBExamTable* in the **Data
    Sources** node of the form. (If it’s not there, make sure you have done a
    **Save all**, and a **Build**, then right click the Data Source name and
    select **Restore**.)

21. Locate the *MBExam* field group and add it under the **Grid** in the
    **Design** node by dragging and dropping respectively.

22. Navigate to the **Default Column** property of the *QuickFilter* and type
    *MBExam_ExamID*.

## Task 2: Create a new Display menu item – MBExamTable

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Add** \> **New Item.**

3.  Under **Dynamics 365 Items**, select **User Interface** and select **Display
    Menu Item**.

4.  In the **Name** field type *MBExamTable* and select the **Add** button.

5.  A new folder **Display Menu Items** will be created in the **Solution
    Explorer** under the project *PrjMB500Lab-2*.

6.  In the **Display Menu Items** folder, a new menu *MBExamTable* will also be
    created.

7.  Open *MBExamTable* menu item in the **Element designer** pane and right
    click on it to select the **Properties** option.

8.  For **Object Type**, select **Form**.

9.  For **Object**, select *MBExamTable*.

10. For **Label**, type *Exam*.

## Task 3: Extend the HRM menu

1.  In the (View \> ) **Application Explorer**, select *HRM* menu under **User
    Interface**.

2.  Right-click on *HRM* menu and select **Create extension**.

3.  A new folder **Menu Extensions** will be created in the **Solution
    Explorer** under the project *PrjMB500Lab-2*.

4.  A new element *HRM.MB500Model* will be created in the **Menu Extensions**
    folder.

5.  Open *HRM.MB500Model* in the **Element designer** pane.

6.  Drag the *MBExamTable* display menu item from the **Solution Explorer** and
    drop it under the *Setup* sub-menu under *HRM.MB500Model*.

## Task 4: Test

1.  In the **Solution Explorer** right click on the project *PrjMB500Lab-2.*

2.  Select **Build.**

3.  Once the build is successful, navigate to the finance and operations apps
    page on your browser and refresh the page.

4.  Select legal entity **USMF**.

5.  Navigate to Modules \> Human resources \> Setup \> Exam

    1.  If you get errors, then go back to your project and **Synchronize** it
        with the database

6.  Use the **New** button in the action pane to create a new exam record.

7.  Use the **Edit** button in the action pane to edit an existing exam record.

8.  Use the **Delete** button in the action pane to delete an existing exam
    record.
