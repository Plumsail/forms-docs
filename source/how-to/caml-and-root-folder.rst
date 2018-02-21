Filtering List or Library by CAML or with Root Folder
=======================================================

.. contents:: Contents:
 :local:
 :depth: 1

Description
--------------------------------------------------
In the :doc:`previous article </how-to/child-parent-form>`, I've shown you how you can filter List or Library displayed results with Lookup, essentially creating a Parent/Children relationship.

In this article, I will show you two alternatives that you can use instead:

1. Filtering by **CAML query**
2. Filtering by **Root Folder**

Both methods can be applied dynamically when the form loads, allowing you to specify what contents you want List or Library to display.

Filtering by CAML query
--------------------------------------------------
| Filtering by CAML Query is very easy. First, you need to know how to use CAML and what it is, you can read about it |CAML|. 
| Also, find information on how to build queries |queries|.

What you need to know, is that CAML filtering is applied when you attach Children items to Parent. So this is essentially the same filtering, 
but you can configure it to anything you like. If you already have filtering by Lookup applied, 
you'll need to modify the query instead of replacing it, otherwise the filtering will be lost.

I will provide several examples of filtering which you can copy or modify according to your needs.

Filtering by Title
**************************************************
This is the simplest scenario, where you just need to filter List or Library by one field only.

This can be done with the following code when List or Library control loads:

.. code-block:: javascript

    fd.spBeforeRender(function() {
        var dt = fd.control('SPDataTable0');
        if (dt.widget) {
            filterDT();
        } else {
            dt.$on('ready', function() {
                filterDT();
            });
        }

        function filterDT(){
            dt.filter = "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
        }
    });

You can also filter List or Library dynamically, for example when the Form's Title changes, to only show items with the same title:

.. code-block:: javascript

    fd.spBeforeRender(function() {
        var dt = fd.control('SPDataTable0');
        if (dt.widget) {
            filterDT();
        } else {
            dt.$on('ready', function() {
                filterDT();
            });
        }

        //filter List or Library with new Title value when Title changes
        fd.field('Title').$on('change', function(value) {
            fd.control('SPDataTable0').filter  = "<Eq><FieldRef Name='Title'/><Value Type='Text'>" + value + "</Value></Eq>";
        });

        function filterDT(){
            dt.filter = "<Eq><FieldRef Name='Title'/><Value Type='Text'>" + fd.field('Title').value + "</Value></Eq>";
        }
    });


Filtering by Title and Number
**************************************************
Filtering by two fields is also easy, you just need to include them both in the code:

.. code-block:: javascript

    fd.spBeforeRender(function() {
        var dt = fd.control('SPDataTable0');
        if (dt.widget) {
            filterDT();
        } else {
            dt.$on('ready', function() {
                filterDT();
            });
        }

        function filterDT(){
            var filter = "<And>";
            filter += "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
            filter += "<Eq><FieldRef Name='ID'/><Value Type='Text'>1</Value></Eq>";
            filter += "</And>";
            dt.filter = filter;
        }
    });

    

You can extend this functionality to however many fields you need, just remember to wrap them inside <And></And> tags.

Filtering by Title and Lookup
**************************************************
How to apply CAML filtering when you already have List or Library filtered with a Lookup?

It's easy, you just need to retrieve the old value first:

.. code-block:: javascript

    fd.spBeforeRender(function() {
        var dt = fd.control('SPDataTable0');
        if (dt.widget) {
            filterDT();
        } else {
            dt.$on('ready', function() {
                filterDT();
            });
        }

        function filterDT(){
            var filter = "<And>"
            //add existing filter value
            filter += dt.filter;
            //add your own filtering conditions
            filter += "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
            filter += "</And>"
            //apply filtering
            dt.filter = filter;
        }
    });

.. |CAML| raw:: html

   <a href="https://msdn.microsoft.com/en-us/library/office/ms426449.aspx" target="_blank">here</a>

.. |queries| raw:: html

   <a href="https://msdn.microsoft.com/en-us/library/office/ms467521.aspx" target="_blank">here</a>

Filtering by Root Folder
--------------------------------------------------