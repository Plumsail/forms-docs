.. title:: Populate column of DataTable in SharePoint form

.. meta::
   :description: Get info from any other SharePoint list inside a DataTable column - this allows you to load items just like a lookup field from any list

How to populate dropdown column of DataTable in SharePoint form with data from any SharePoint list
======================================================================================================

In this article, we'll show you how to load values from SharePoint List and display them in DataTable control dropdowns.

Essentially, this works similar to Lookup fields, but the values are stored as text, 
and if something changes in the source lists, the values in DataTable will stay the same.

This functionality also supports filtering and cascading selection, which we'll showcase in the article.

|pic0|

.. |pic0| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-0-anim.gif
   :alt: Animated DataTable

.. contents::
 :local:
 :depth: 1
 
Source Lists
--------------------------------------------------
First, create three SharePoint Lists - **Categories, Products and Orders**.

**Categories** List will contain two columns - Title and License (Choice):

|pic1|

.. |pic1| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-1-categories.png
   :alt: Categories List

**Products** List will contain two columns as well - Title and Category (Lookup):

|pic2|

.. |pic2| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-2-products.png
   :alt: Products List

Finally, **Orders** will also contain two columns - Title and License (Choice):

|pic3|

.. |pic3| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-3-orders.png
   :alt: Products List

Form Configuration
--------------------------------------------------
Open Orders List in editor and customize forms, add Title and License.

Then, add DataTable control, customize its Form, add Category and Product columns to DataTable, 
set them to Type: *Dropdown* and don't forget to change their Internal Name to match title:

|pic4|

.. |pic4| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-4-form.png
   :alt: Match Internal Name

Populating Dropdown
------------------------

To populate the Category dropdown column of DataTable control with data from **Categories** list, we use |PnPjs library| that is built into Plumsail Forms. 
Here is the code:

.. code-block:: javascript

    fd.spRendered(function() {
        fd.control('DataTable1').$on('edit', function(e) {
            if (e.column.field === 'Category') {
                //pass widget + current Category value 
                populateCategories(e.widget, e.model.Category);
            }
        })
        
    });

    function populateCategories(widget, value) {
        //will show as loading
        widget._showBusy();
        
        sp.web.lists.getByTitle('Categories').items
            .select('ID', 'Title')
            .get()
            .then(function(items) {
                //set options
                widget.setDataSource({
                    data: items.map(function(i) { return i.Title })
                });

                //set value if one was select
                widget.value(value);
                //hide loading state
                widget._hideBusy();
            });
    }

Cascading Dropdowns
-----------------------

To display only products that belongs to the selected category, apply filtering to the data from **Products** list:

.. code-block:: javascript

    fd.spRendered(function() {
        fd.control('DataTable1').$on('edit', function(e) {
            if (e.column.field === 'Category') {
                //pass widget + current Category value 
                populateCategories(e.widget, e.model.Category);
            }
            
            if (e.column.field === 'Product') {
                //pass widget + current Category and Product value 
                populateProducts(e.widget, e.model.Category, e.model.Product);
            }
        })
        
    });

    function populateCategories(widget, value) {
        //will show as loading
        widget._showBusy();

        sp.web.lists.getByTitle('Categories').items
            .select('ID', 'Title')
            .get()
            .then(function(items) {
                //set options
                widget.setDataSource({
                    data: items.map(function(i) { return i.Title })
                });

                //set value if one was select
                widget.value(value);
                //hide loading state
                widget._hideBusy();
            });
    }

    function populateProducts(widget, parentValue, value) {
        //will show as loading
        widget._showBusy();
        
        sp.web.lists.getByTitle('Products').items
            .select('ID', 'Title', 'Category/Title')
            .expand('Category')
            .filter("Category/Title eq '" + parentValue + "'")
            .get()
            .then(function(items) {
                widget.setDataSource({
                    data: items.map(function(i) { return i.Title })
                });
                
                //set value if one was select
                widget.value(value);
                //hide loading state
                widget._hideBusy();
            });
    }

The value for the DataTable can then be stored either in hidden SharePoint field or in Multiline Plain Text column:

|pic6|

.. |pic6| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-6-save.png
   :alt: SaveTo property

If you store data in column, you will see it displayed in List view with the help of our automatic :doc:`customizers </how-to/save-table-signature>`:

|pic7|

.. |pic7| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-7-column.png
   :alt: Column with table in List View

Here's how our form would look like in the browser:

|pic5|

.. |pic5| image:: ../images/how-to/dynamic-datatable/dynamic-datatable-5-result.png
   :alt: Form with DataTable result

.. |PnPjs library| raw:: html

    <a href="https://pnp.github.io/pnpjs/" target="_blank">PnPjs library</a>