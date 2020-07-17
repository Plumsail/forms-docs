.. title:: Filter List or Library by CAML in a SharePoint form 

.. meta::
   :description: Examples on how to filter List or Library control by one field, by one field dynamically, by multiple fields, add filter with lookup filter already applied, and more

How to filter items or documents by CAML in List or Library control
=================================================================================

.. contents:: Contents:
 :local:
 :depth: 1

Introduction
--------------------------------------------------
In this article, I will show you how to filter by CAML.

This method can be applied dynamically and when the form loads, allowing you to specify what contents you want List or Library to display at any time.

| Filtering by CAML Query is very easy. First, you need to know how to use CAML and what it is, you can read about it |CAML|. 
| Also, find information on how to build queries |queries|.

What you need to know, is that CAML filtering is applied when you attach Children items to Parent. So this is essentially the same filtering, 
but you can configure it to anything you like. If you already have filtering by Lookup applied, 
you'll need to modify the query instead of replacing it, otherwise the filtering will be lost.

Read more about properties and events in :ref:`javascript-listorlibrary` JavaScript documentation.

In this article you will find several examples of filtering which you can copy or modify according to your needs.

Filter by one field
--------------------------------------------------
This is the simplest scenario, where you just need to filter List or Library by one field only.

This can be done with the following code when List or Library control loads:

.. code-block:: javascript

    fd.spRendered(function() {
        var dt = fd.control('SPDataTable0');
        dt.ready().then(function() {
            filterDT();
        });

        function filterDT(){
            dt.filter = "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
            dt.refresh();
        }
    });


Filter by one field dynamically
--------------------------------------------------

You can also filter List or Library dynamically. For example, you have Search field and want to only show items where Title contains input in Search field:

.. code-block:: javascript

    fd.spRendered(function() {
        var dt = fd.control('SPDataTable0');
        dt.ready().then(function() {
            filterDT();
        });

        //filter List or Library with new value when Search field changes
        fd.field('Search').$on('change', function() {
            filterDT();
        });

        function filterDT(){
            dt.filter = "<Contains><FieldRef Name='Title'/><Value Type='Text'>" 
                + fd.field('Search').value + "</Value></Contains>";
            dt.refresh();
        }
    });


Filter by several fields
--------------------------------------------------
Filtering by two fields is also easy, you just need to include them both in the code:

.. code-block:: javascript

    fd.spRendered(function() {
        var dt = fd.control('SPDataTable0');
        dt.ready().then(function() {
            filterDT();
        });

        function filterDT(){
            var filter = "<And>";
            filter += "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
            filter += "<Eq><FieldRef Name='ID'/><Value Type='Text'>1</Value></Eq>";
            filter += "</And>";
            dt.filter = filter;
            dt.refresh();
        }
    });

    

You can extend this functionality to however many fields you need, just remember to wrap them inside <And></And> tags.

Filter, but keep Lookup settings
--------------------------------------------------
How to apply CAML filtering when you already have List or Library filtered with a Lookup?

It's easy, you just need to retrieve the old value first:

.. code-block:: javascript

    fd.spRendered(function() {
        var dt = fd.control('SPDataTable0');
        dt.ready().then(function() {
            filterDT();
        });

        function filterDT(){
            var filter = "<And>"
            //add existing filter value
            filter += dt.filter;
            //add your own filtering conditions
            filter += "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
            filter += "</And>"
            //apply filtering
            dt.filter = filter;
            dt.refresh();
        }
    });

Filter number between Min and Max
--------------------------------------------------
Another thing that you can filter can be a range. For example, you have a list of products and you only want to display products within a certain price range.

If you have Min and Max fields on your form, this can be easily done with the following code:

.. code-block:: javascript

    fd.spRendered(function() {
        var dt = fd.control('SPDataTable0');
        dt.ready().then(function() {
            filterDT();
        });

        //filter List or Library with new value when Min field changes
        fd.field('Min').$on('change', function() {
            filterDT();
        });

        //filter List or Library with new value when Max field changes
        fd.field('Max').$on('change', function() {
            filterDT();
        });

        function filterDT(){
            var filter = "<And>"

            //greater or equal than Min value
            filter += "<Geq><FieldRef Name='Value'/><Value Type='Integer'>" + fd.field('Min').value + "</Value></Geq>";
            //lesser or equal than Max value
            filter += "<Leq><FieldRef Name='Value'/><Value Type='Integer'>" + fd.field('Max').value + "</Value></Leq>";
            filter += "</And>"

            //apply filtering
            dt.filter = filter;
            dt.refresh();
        }
    });

Filter date between From and To
--------------------------------------------------
Same range filtering can be applied to Dates. For example, you might want to see all documents uploaded between two dates.

You can do it with the following code:

.. code-block:: javascript

    fd.spRendered(function() {
        var dt = fd.control('SPDataTable0');
        dt.ready().then(function() {
            filterDT();
        });

        //filter List or Library with new value when From field changes
        fd.field('From').$on('change', function() {
            filterDT();
        });

        //filter List or Library with new value when To field changes
        fd.field('To').$on('change', function() {
            filterDT();
        });

        function filterDT(){
            var filter = "<And>"
             
            //format dates to ISO string for filtering
            var toDate = fd.field('To').value.toISOString();
            var fromDate = fd.field('From').value.toISOString();

            //strictly greater than From value
            filter += "<Gt><FieldRef Name='Created'/><Value Type='DateTime'>" + fromDate + "</Value></Gt>";
            //strictly lesser than To value
            filter += "<Lt><FieldRef Name='Created'/><Value Type='DateTime'>" + toDate + "</Value></Lt>";
            filter += "</And>"

            //apply filtering
            dt.filter = filter;
            dt.refresh();
        }
    });

.. |CAML| raw:: html

   <a href="https://msdn.microsoft.com/en-us/library/office/ms426449.aspx" target="_blank">here</a>

.. |queries| raw:: html

   <a href="https://msdn.microsoft.com/en-us/library/office/ms467521.aspx" target="_blank">here</a>
