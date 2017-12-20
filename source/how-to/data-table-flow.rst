Convert form with DataTable into PDF and send for approval
===========================================================

Description
--------------------------------------------------

With recently added :ref:`designer-datatable` control, we can design a more complex form and then submit it to Flow.

In this example, we will design an Expense Reimbursement Form, which will include DataTable to list all the expenses,
as well as Ink Sketch controls to get signatures from the user and his supervisor.

Design a form
--------------------------------------------------
First, we will design a form, which will include all the necessary information from the employee, such as name, ID, Department, and the purpose behind the expenses.
We will also include two date fields From and To, which will include time period during which the expenses took place.

Next, our form will have DataTable to store all the expenses and will include Description, Category and Cost.

After the table, we will have Total field which will automatically calculate and display Total amount of expenses.

Finally, the form will include a signature pad for the employee to sign the form.