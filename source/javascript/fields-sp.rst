SharePoint Fields
==================================================

Intro
--------------------------------------------------
In this section you will find how to get information from SharePoint fields, how to set their value, how to detect changes in SharePoint fields and much more using JavaScript.

A lot of properties and events are shared between :doc:`Plumsail Fields </javascript/fields>` and SharePoint fields, but some things are unique to SharePoint fields.

Here you can find the most complete information on SharePoint fields.

*Internal Name* is the property that is used to identify specific fields and apply methods to them. *Internal Name* is unique for every element on the form.

**Important!** These events, methods and properties shouldn't be used on their own, they must be executed inside events 
like **spRendered()** or **spBeforeSave()** in order to actually access the fields or controls that you target.

If you just add these scripts on their own or inside wrong event in JavaScript editor,
they will not have access to the specified fields, or will execute at the wrong time.
Read more about different events in :doc:`Manager section </javascript/manager>`.

Single Line of Text
**************************************************

.. list-table::
    :widths: 10 80  
        

    *   -   **Get**
        - .. code-block:: javascript

                fd.field('SingleLine').value;

    *   -   **Set**
        - .. code-block:: javascript

                fd.field('SingleLine').value = "New Text";

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('SingleLine').$on('change', function(value) {
                    alert('New value: ' + value);
                });


Multiline Text Field
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get**
        - .. code-block:: javascript

                fd.field('MultipleLines').value;

    *   -   **Set**
        - .. code-block:: javascript

                fd.field('MultipleLines').value = "New Text";

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('MultipleLines').$on('change', function(value) {
                    alert('New value: ' + value);
                });
                
Choice Single - Dropdown or Radio
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get**
        - .. code-block:: javascript

                fd.field('ChoiceSingle').value;

    *   -   **Set**
        - .. code-block:: javascript

                fd.field('ChoiceSingle').value = "Enter Choice #2";

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('ChoiceSingle').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Choice Multiple - Checkboxes
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get**
        - .. code-block:: javascript

                // returns an array of choices:
                fd.field('ChoiceMultiple').value; 

    *   -   **Set**
        - .. code-block:: javascript

                fd.field('ChoiceMultiple').value 
                = ["Enter Choice #1", "Enter Choice #2"];

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('ChoiceMultiple').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Number/Currency
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get**
        - .. code-block:: javascript

            // returns number as a string:
            fd.field('Number').value; 

    *   -   **Set**
        - .. code-block:: javascript

            fd.field('Number').value = "256";

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('Number').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Date
**************************************************

.. list-table::
    :widths: 10 90
        

    *   -   **Get**
        - .. code-block:: javascript

                // returns Date object:
                fd.field('Date').value; 

    *   -   **Set**
        - .. code-block:: javascript

                fd.field('Date').value = new Date();

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('Date').$on('change', function(value) {
                    alert('New value: ' + value.toLocaleDateString());
                });

DateTime
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get**
        - .. code-block:: javascript

                // returns Date object:
                fd.field('DateTime').value; 

    *   -   **Set**
        - .. code-block:: javascript

                fd.field('DateTime').value = new Date().setHours(13, 31, 0);

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('Date').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Lookup
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get ID**
        - .. code-block:: javascript

                // returns ID of the selected element:
                fd.field('Lookup').value; 

    *   -   **Get Text**
        - .. code-block:: javascript

                // returns selected element as string:
                fd.field('Lookup').selected.LookupValue; 

    *   -   **Set**
        - .. code-block:: javascript

                //set element with the ID:
                fd.field('Lookup').value = 1

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('Lookup').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Multi Lookup
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get All Text**
        - .. code-block:: javascript

                var selected = fd.field('LookupMulti').selected;
                var s = '';
                for (var i = 0; i < selected.length; i++) {
                    s += selected[i].LookupValue + '; ';
                }
                alert(s);

    *   -   **Get First Text**
        - .. code-block:: javascript

                // returns first selected element as string:
                fd.field('LookupMulti').selected[0].LookupValue; 

    *   -   **Get Second Text**
        - .. code-block:: javascript

                // returns second selected element as string:
                fd.field('LookupMulti').selected[1].LookupValue;

    *   -   **Get all IDs**
        - .. code-block:: javascript

                var selectedIDs = fd.field('LookupMulti').value;
                var s = '';
                for (var i = 0; i < selectedIDs.length; i++) {
                    s += selectedIDs[i] + '; ';
                }
                alert(s);

    *   -   **Get first ID**
        - .. code-block:: javascript

                fd.field('LookupMulti').value[0];

    *   -   **Set**
        - .. code-block:: javascript

                //set with an array of IDs:
                fd.field('LookupMulti').value = ["2", "3", "4"];

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('LookupMulti').$on('change', function(value) {
                    alert('New value: ' + value);
                });


Boolean - Yes/No
**************************************************

.. list-table::
    :widths: 10 80    
        

    *   -   **Get**
        - .. code-block:: javascript

                // returns true or false:
                fd.field('Boolean').value; 

    *   -   **Set**
        - .. code-block:: javascript

                // can set with true/false:
                fd.field('Boolean').value = false;

                // can set with 0/1:
                fd.field('Boolean').value = 1; 

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('Boolean').$on('change', function(value) {
                    alert('New value: ' + value);
                });

People Picker
**************************************************
Add **$on('ready',function(){})** event if you want to run these methods when page loads:

.. list-table::
    :widths: 10 80    
        

    *   -   **Get All Names**
        - .. code-block:: javascript

                //will run once the field is initialized:
                fd.field('Persons').$on('ready',function(field) {
                    var people = fd.field('Persons').value;
                    var s = '';
                    for (var i = 0; i < people.length; i++) {
                        s += people[i].DisplayText + '; ';
                    }
                    alert(s);
                });

    *   -   **Get Email from First User**
        - .. code-block:: javascript

                fd.field('Persons').value[0].EntityData.Email;

    *   -   **Set**
        - .. code-block:: javascript

                // assign value by a display name
                fd.field('Persons').value = "John Smith";

                // or by an e-mail:
                fd.field('Persons').value = "john.smith@mail.com";

    *   -   **OnChange**
        - .. code-block:: javascript

                fd.field('Persons').$on('change', function(value) {
                    var people = value;
                    var s = '';
                    for (var i = 0; i < people.length; i++) {
                        s += people[i].DisplayText + '; ';
                    }
                    alert('New value: ' + s);
                });