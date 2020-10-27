.. title:: Сreate SharePoint items from Data Table rows with Power Automate

.. meta::
   :description: Use Microsoft Power Automate to create items in SharePoint from public web form's Data Table rows - each row becomes its own item

How to create SharePoint list items from Data Table rows with Power Automate 
=======================================================================================

We've discussed how a form with DataTable can be :doc:`converted into PDF and sent via email</how-to/data-table-convert-html>`, 
now we'll use DataTable to add items to SharePoint.

We'll create an Office Supplies Request form which when submitted will create items in two SharePoint lists - Orders and Ordered Items.
As you might've guessed, general information from the form will go into orders 
while specific information about each record in DataTable will create an item in Ordered Items list. Ordered Items will have a lookup to tie them to the Order.

.. contents::
 :local:
 :depth: 1

Form and Form's Logic
--------------------------------------------------
The Form will be fairly straightforward - we need the department of the company, location to be delivered to, who've made the request, 
date all items have to be delivered, and finally the table itself.

I will also include Order Total field to calculate total value of the order and here's our form:

.. image:: ../images/how-to/data-table-to-sp/1_Designer.png
   :alt: Form inside the designer

|

.. Note:: If you want to find out how to add Line total and Overall total calculation to this form, please, check out our :doc:`how to work with Data Table using JS article <./data-table-cases>`.

SharePoint Lists
--------------------------------------------------
In order to save data to SharePoint, we need two SharePoint Lists - Orders and Ordered Items.

Orders should have Title, Department, Destination, Requester, Date Needed, and Order Total columns:

.. image:: ../images/how-to/data-table-to-sp/2_Orders.png
   :alt: Orders

|

Order Items List on the other hand has to have Title, Amount, Price, Total, Destination and Order columns:

.. image:: ../images/how-to/data-table-to-sp/3_Order_Items.png
   :alt: Order Items

|

Now, that the form and lists are ready, it is time to create custom Flow and let it populate lists with data.

Flow
--------------------------------------------------
We will use Flow to first create an Order and then add each record as an item to Order Items.

If you haven't read our introduction to using Power Automate (MS Flow) with Plumsail Forms, you can find information on how to add our custom connector :doc:`here </microsoft-flow>`.

You can also find information about how to subscribe to Form submission in the :ref:`creating-flow` section.

Once you've subscribed and parsed JSON from the Form, click **Add an action** and search for *SharePoint*. 
We'll need to add *SharePoint - Create Item*, select our Orders list and fill in all the columns with Form fields, like this:

.. image:: ../images/how-to/data-table-to-sp/4_Create_Order.png
   :alt: Create Order

|

To make Title unique I've added Date Needed to it, with formatting:

.. code-block:: javascript

    formatDateTime(body('Parse_JSON')?['DateNeeded'], 'MM/dd/yyyy')

Next, we search and select *SharePoint - Create Item* once again, this time we choose Order Items list and start filling in all the columns. 
Once we add any column from our DataTable, the action will automatically be transformed to run as many times as there are records in the DataTable:

.. image:: ../images/how-to/data-table-to-sp/5_Create_Order_Items.png
   :alt: Create Order Items

|

Everything else is fairly straightforward, when filling in Order lookup column, we need to select to add custom value and fill in the ID from our previous Item created.

That's pretty much it, now we can click **Save Flow** and run some tests.

Result
--------------------------------------------------
So, here's my form in the browser, filled in with the test data:

.. image:: ../images/how-to/data-table-to-sp/6_Form_Test.png
   :alt: Form in a browser

|

I press submit, then the Flow processes the request. There are no errors, so everything went smoothly.

Here's an item created in SharePoint Order List:

.. image:: ../images/how-to/data-table-to-sp/7_Result_Order.png
   :alt: Order List result

|

And here are all the items added to the Order Items List, all tied to the Order itself with a Lookup:

.. image:: ../images/how-to/data-table-to-sp/8_Result_Items.png
   :alt: Ordered Items List result

|