Create an item in SharePoint List
==================================================

Description
--------------------------------------------------
One of the simplest and very practical use cases for Plumsail Forms might be adding items to SharePoint Lists.
You are not tied to SharePoint forms, items can be added from the Flow.

In this example, we will design a form for customers to subscribe to some form of updates from your company
and use Flow to add this information to a list on your SharePoint site.

Preparation
--------------------------------------------------
First step is to design a list, if you don't have one. It's best to start from the list, 
so you know what fields you will need on your form rather than another way around.

I will design simple list with three extra Single line plain text columns:

.. image:: ../images/how-to/email/0_CreateList.png
   :alt: Create List

|

Next, after designing the list, create Plumsail form in Forms Designer. 
You can also design Modern SharePoint form if you want to create items in the different list when you submit this one, 
but you'll need to Submit Data to Flow in General Settings.

I've designed this simple form:

.. image:: ../images/how-to/email/1_DesignForm.png
   :alt: Design Form

|

Now, after the form is saved, it is time to configure Flow.

Configure the Flow
--------------------------------------------------

First, open Microsoft Flow page and go to My Flows:

.. image:: ../images/how-to/email/2_MyFlows.png
   :alt: My Flows

|

On My Flows page, click *Create from blank* to create new Flow:

.. image:: ../images/how-to/email/3_CreateFromBlank.png
   :alt: Create from blank

|

We'll need to find the correct trigger for Forms Submission. Click *Search*:

.. image:: ../images/how-to/email/4_Search.png
   :alt: Search

|

Search for *Plumsail* and you'll find the right one - *Plumsail Forms - Form is submitted*. Add it:

.. image:: ../images/how-to/email/5_AddPlumsailTrigger.png
   :alt: Add Plumsail trigger

|

Next, you need to fill in Form ID. It can be found in **General Settings** in the designer. Click *Add an action* when you fill in the ID:

.. image:: ../images/how-to/email/7_AddID.png
   :alt: Add ID from General Settings

|

We need to somehow parse JSON received from form submission to use it in email. 
Search for *JSON* and you'll find the action that you need - *Data Operations - Parse JSON*. Add it:

.. image:: ../images/how-to/email/8_JSON.png
   :alt: Parse JSON

|

Here, you'll need to click on *Content* field and select Body from menu on the right. Next, go to **General settings** in the designer and copy form's schema.
Don't forget to save the form first, if you've added some changes, that will update the schema. Copy the schema and click *Add an action*:

.. image:: ../images/how-to/email/9_ContentAndSchema.png
   :alt: Add Content and Schema from General Settings

|

We'll use Microsoft's *SharePoint - Create item* action to create an item in a list. Select it:

.. image:: ../images/how-to/file/2_SharePointCreateItem.png
   :alt: SharePoint - Create item

|

You will need to add your site address. If it's your first time configuring SharePoint action, 
select *Enter custom value* in dropdown menu and type in or copy and paste your site address, something like *https://mydomain.sharepoint.com/sites/mysite*

You will also need to select List in List Name field:

.. image:: ../images/how-to/file/3_SiteAddressEnterCustomValue.png
   :alt: Site Address and List Name

|

Now you will see a menu with all columns that can be filled with Flow. 
Some columns are an exception and cannot be filled using this action, for example, Choice column. We advice to use columns that can be filled.

In our case, we have Title and three more Single line text columns, these can be easily filled. Select information from the form in menu on the right.

You might have noticed that I used Checkboxes on my form and they produce an array of strings as an output.
If I were to simply add this value to any of the fields, it would result in multiple actions performed for each value in the array. 

It's not a bad option and might be useful in some situations, but if you have lots of Checkboxes on your form, it can quickly get out of hand.

Here, I will use Expression of Workflow Definition Language to combine every value from the array into single string.
In menu on the right, instead of clicking on the field, click Expression and type in **join()**:

.. image:: ../images/how-to/file/4_Expression.png
   :alt: Site Address and List Name

|

Now go back to Dynamic content tab, place the *caret* (a.k.a. the *cursor*) between the round brackets and click on field you want to join as a string.

You can also add a delimiter between each string, I've added **', '** as a delimiter.

Here is the result:

.. image:: ../images/how-to/file/5_Join.png
   :alt: Join Expression

|

Final result should look like this:

.. image:: ../images/how-to/file/6_Final.png
   :alt: Final

|

Now you can click *Save Flow* and **Done**.

Final Result
--------------------------------------------------
Make sure that the Flow is active and open Form preview. I've filled mine with example data and clicked *Submit*:

.. image:: ../images/how-to/file/7_ExampleForm.png
   :alt: Example Form

|

Once the Form is submitted and processed with Flow, which can take some time, depending on how complex your form is, I get this result:

.. image:: ../images/how-to/file/8_Result.png
   :alt: Result

|

This example is simple, but you've seen how an item can be added to the list and how to convert array of strings into one string.
This can be used in combination with any other Flow, for example, you can also :doc:`send an email after form is submitted </how-to/email>` and item is created.

