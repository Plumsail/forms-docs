Save Ink Sketch and DataTable controls to hidden SharePoint fields
===========================================================================

.. contents:: Contents:
 :local:
 :depth: 1

Description
--------------------------------------------------
Starting with version 1.1.6, it's now possible to save Ink Sketch and DataTable controls 
to hidden SharePoint fields when using them on a SharePoint Form. This means that the data will be saved when the form is saved.

These fields can be created and deleted right in the designer when editing settings for one of the controls.

How to configure
--------------------------------------------------
Select an Ink Sketch or a DataTable control and you'll see SaveTo property:

.. image:: ../images/how-to/save-table-signature/SaveTo.png
   :alt: SaveTo property

*If the form was created with an older version of Forms, simply delete the control and add it again.*

Inside the dropdown you can select one of existing hidden fields to store data to (it must be a Multiline Text field to work) or create a new field:

.. image:: ../images/how-to/save-table-signature/AddNew.png
   :alt: Add new fields

*New field will be called fd_Signature_InternalName or fd_DataTable_InternalName depending on the type of the field.*

If you want to delete one of the hidden fields, you can do it by selecting "🖉 Manage" option in the dropdown. 

.. image:: ../images/how-to/save-table-signature/ManageFields.png
   :alt: Delete hidden fields

*System fields cannot be deleted this way, but be careful not to delete one of important fields by accident. Old data is not transfered to new field automatically.*