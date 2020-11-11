.. title:: Manipulate fields in inline editing mode of List or Library

.. meta::
   :description: How to work with fields when editing List or Library in Inline mode - e.g. prepopulate fields, set fields based on changes in other fields, filter lookup fields

How to manipulate fields in inline editing mode of List or Library control
===========================================================================

In this article, I will show you how to work with List or Library control in the Inline editing mode.  

You will know how to prepopulate fields, set fields based on changes in other fields, filter lookup fields within a List or Library control. 

.. contents::
 :local:
 :depth: 1

Populating fields of a new row in List or Library control 
----------------------------------------------------------------------

|pic1|

.. |pic1| image:: ../images/how-to/list-or-library-inline/how-to-list-or-library-inline-populate-fields.gif
   :alt: Populating fields of a new row

First, we want to prepopulate the Due Date and Assigned To fields in a new List or Library row with the current form field values. 

To handle switching a row into Inline editing mode, we will use the edit event of the List or Library control. Since we're prepopulating fields of a new record only, we will check the form type. 

Find more information about the |edit event|.  

.. |edit event| raw:: html

    <a href="https://plumsail.com/docs/forms-sp/javascript/controls.html#list-or-library" target="_blank">edit event</a>

.. code-block:: javascript

    //prepopulating fields of a new record  
    //with the values from the parent form
    //when a new item created

    fd.spRendered(function() {
        //prepopulating fields of a new record
        //with the values from the parent form 
        fd.control('SPDataTable1').$on('edit', function(editData) {
            //check that this is a new record
            if (editData.formType === 'New') {
                //prepopulating due date
                editData.field('TaskDueDate').value = fd.field('TaskDueDate').value;
                //prepopulating AssignedTo field
                editData.field('AssignedTo').ready().then(function() {
                    editData.field('AssignedTo').value = fd.field('AssignedTo').value;
                });
            } 
        });
    });

Populating fields based on other fields in List or Library control 
----------------------------------------------------------------------

|pic2|

.. |pic2| image:: ../images/how-to/list-or-library-inline/how-to-list-or-library-inline-change-field.gif
   :alt: Populating fields based on other fields

Next, we want to set the Resolution Date to the current date when a user changes the Status field to 'Completed'.  

As in the previous example, we will use the 'edit' event of the List or Library control and 'change' event of the Status field. 

.. code-block:: javascript

    fd.spRendered(function() { 
        fd.control('SPDataTable1').$on('edit', function(editData) {
            //Set Resolutiondate field value when TaskStatus field changes
            editData.field('TaskStatus').$on('change', function(value) {
                if (value === 'Completed') {
                    editData.field('Resolutiondate').value = new Date();
                } else {
                    editData.field('Resolutiondate').value = null;
                }
            });
        });
    });

Filtering lookup fields in List or Library control  
----------------------------------------------------------------------

|pic3|

.. |pic3| image:: ../images/how-to/list-or-library-inline/how-to-list-or-library-inline-lookup-filter.gif
   :alt: Filtering lookup fields

Finally, in the 'edit' event, we can dynamically filter lookup values in the List or Library control. In this example, we will filter the Office lookup field by the selected City field. Here is the code:

.. code-block:: javascript

    fd.spRendered(function() {
        fd.control('SPDataTable1').$on('edit', function(editData) {
            //filter Office field by City
            editData.field('Office').filter = "City/Id eq '" + fd.field("City").value.LookupId + "'";
            editData.field('Office').useCustomFilterOnly = true;
        });
    }); 