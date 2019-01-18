SharePoint Fields
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

General Info
-------------------------------------------------------------
SharePoint fields are based on the columns of the SharePoint List or Library that you connect to. 
These fields, when added to the form, are automatically connected to the List and will retrieve data from the List, as well as automatically submit user input on save.

It's recommended to only use SharePoint fields on SharePoint forms unless you want to handle data from the Common fields with JavaScript or Flow.
This section contains information about settings for fields that are unique to SharePoint. 

For general information about field properties, check out the :doc:`Fields </designer/fields>` section.

.. _designer-lookup:

Lookup
-------------------------------------------------------------
Lookup field has received several new features, all of which can be configured in the designer.

Now, users can use search bar to filter the selection in the lookup field. 
There's also an option to add new items to the source list, if the item wasn't found - this could be turned on/off.

|example|

.. |example| image:: ../images/how-to/lookup-view/lookup.png
   :alt: Example Lookup

Lookup unique properties
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Lookup field has the following unique settings:

SETTINGS

.. list-table::
    :widths: 10 40

    *   - Operator
        - Determines how the search is handled by the lookup. Has two options: StartsWith - only show items that start with the entered value, Contains - show all items that contain the entered value.
    *   - Add New
        - Allows users to add new values to the source list of the Lookup. User must enter value that doesn't exist yet, then there will be an option to add new item.
    *   - Extra Fields
        - Select fields from the list that also need to be loaded. By default, only ID and 'Display Field' are retrieved. Extra fields can accessed with JavaScript. When adding Lookup fields in Extra Fields setting, do not forget to format them like this: **Category/ID**, **Category/Title**. Uses OData *$select* query option - read more |REST|.
    *   - Expand
        - In the Expand setting you need to enter the Lookup field that you are getting in Extra Fields, such as: **Category**. Uses OData *$expand* query option.


.. |REST| raw:: html

   <a href="https://docs.microsoft.com/en-us/sharepoint/dev/sp-add-ins/use-odata-query-operations-in-sharepoint-rest-requests#select-fields-to-return/" target="_blank">here</a>