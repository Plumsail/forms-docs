Form Sets
=========================================

.. contents:: Contents:
 :local:
 :depth: 1

General Info
-------------------------------------------------------------
Form Sets allow you to design additional forms for SharePoint List or Library. 

By default, each List only has three forms - New, Edit and Display. 
Each additional Form Set allows you to add three more forms - also New, Edit and Display, but a Form Set doesn't have to contain all three forms, it can be just one or two.

You can have as many Form Sets as necessary. You can also either manually redirect users to a Form Set with JavaScript 
or automatically redirect users from certain SharePoint groups to a specific Form Set.

.. image:: ../images/designer/form-sets/1-UI.png
   :alt: Form Sets UI

You can select currently active Form Set in an upper right corner, in the drop-down.

Default Form Set is what all users see if they are not redirected to another Form Set straight way.

You can add new Form Set by clicking **+** sign next to the currently selected Form Set. Clicking Pen Icon allows you to edit properties of the currently selected Form Set.
Trash bin icon allows you to delete the Form Set.

After creating a Form Set, do not forget to save every form you plan to use or it might be missing.

Automatic routing based on SharePoint group membership
-------------------------------------------------------------
When you create a Form Set, straight away, you can configure automatic routing for the members of certain groups:

.. image:: ../images/designer/form-sets/2-FormSetsConfig.png
   :alt: Form Sets Configuration

* Name - the name of the Form Set, can be anything you want, just makes it easier to find among all the Form Sets.
* Order - determines the order in which to open Form Sets if conditions are met. The lower the Order value, the higher the priority for Form Set to open.
* Open forms when a user belongs... - select all groups user must belong to in order to be redirected. **Note!** Must select something in order for redirection to work.
* Excluding the selected groups - will not redirect the user that belongs to the previously picked groups, if the user also belongs to one of the groups selected here.