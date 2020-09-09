.. title:: Automatically bind items or documents to parent

.. meta::
   :description: How to bind items and files in List or Library to parent item or document - create items or upload documents from the form, and associate them with current item

How to create SharePoint form with associated items or documents and bind new ones automatically
===================================================================================================

This article will describe how you can use :ref:`designer-listorlibrary` control from the form to create Child elements and bind them to Parent.

This means that you can add new Items or Documents from the Form straight into related SharePoint List or Document Library, 
and automatically attach them to the current Item or Document with a Lookup. When you open this Item again, you will only see bound elements in List or Library control. 

This can serve as alternative to attachments or to create complex relationships between items. 

With **List or Library** control this is very easy to do, just follow the steps described below.

.. contents::
 :local:
 :depth: 1

Bind children to parent
--------------------------------------------------
| First, create Lists that you want to use as Parent List and Children List. You can use Lists or Document Libraries for this.
| In the Children List/Library create a Lookup column and select *Get information from:* Parent List. You can choose any field to display such as Title or ID.

.. image:: ../images/how-to/child-parent-form/lookup.png
   :alt: Parent and Children Lists

|

Design forms for both Parent and Children Lists, including New, Edit and Display forms. Document Libraries only need Edit and Display forms.
   
Do not add the lookup to the Child form, as you don't want users to change it manually.

.. image:: ../images/how-to/child-parent-form/parentform.png
   :alt: Parent Form

|

Finally, add List or Library control to the Parent forms. In SETTINGS → DataSource, select *List:* Children List and *Lookup Field*: Parent lookup.

.. image:: ../images/how-to/child-parent-form/datasource.png
   :alt: Data Source configuration

|

This will ensure that when you open Parent Edit or Display Form, you will only see connected items in the List or Library control.

Connecting Child to Parent happens automatically, in Edit and Display forms it happens straight away, but in New Form, 
you must first save Parent and then added items will be tied to Parent. All this happens automatically without any additional configuration.

.. image:: ../images/how-to/child-parent-form/result.png
   :alt: Parent Form with Children

|

You can upload multiple documents at once - simply select multiple files on your machine.
Uploaded documents also get connected to Parent via Lookup, so this functionality is the same for both Lists and Libraries.

.. image:: ../images/how-to/child-parent-form/docs.png
   :alt: Parent Form with Uploaded Documents
