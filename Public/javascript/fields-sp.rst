SharePoint Fields
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

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
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                //returns string
                fd.field('SingleLine').value;
                fd.field('SingleLine').value = "New Text";

    *   -   **$on('change')**
        -   Triggers on 'change' event.

            
            |

            *Examples:*

            .. code-block:: javascript

                fd.field('SingleLine').$on('change', function(value) {
                    alert('New value: ' + value);
                });


Multiline Text Field
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                //returns a string of text with formatting
                fd.field('MultipleLines').value;
                fd.field('MultipleLines').value = "New Text";

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('MultipleLines').$on('change', function(value) {
                    alert('New value: ' + value);
                });
                
Choice Single - Dropdown or Radio
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                //returns selected choice as a string
                fd.field('ChoiceSingle').value;
                fd.field('ChoiceSingle').value = "Enter Choice #2";

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('ChoiceSingle').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Choice Multiple - Checkboxes
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns an array of choices:
                fd.field('ChoiceMultiple').value; 
                fd.field('ChoiceMultiple').value = ["Enter Choice #1", "Enter Choice #2"];

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('ChoiceMultiple').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Number/Currency
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns number as a string:
                fd.field('Number').value; 
                fd.field('Number').value = "256";

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Number').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Date
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples

    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns Date object:
                fd.field('Date').value; 
                fd.field('Date').value = new Date();

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Date').$on('change', function(value) {
                    alert('New value: ' + value.toLocaleDateString());
                });

DateTime
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples

    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns Date object:
                fd.field('DateTime').value; 
                fd.field('DateTime').value = new Date().setHours(13, 31, 0);

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Date').$on('change', function(value) {
                    alert('New value: ' + value);
                });

Lookup/LookupMulti
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            Returns an object for Single Choice Lookup, returns an array of objects for Multiple Choice Lookups. 

            Can be set with Item ID or an array of item IDs for Multiple Choice Lookups.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //SINGLE CHOICE LOOKUP

                // returns an ID of the selected element:
                fd.field('Lookup').value; 

                // returns the selected element as a string:
                fd.field('Lookup').value.LookupValue;

                // select element with the ID:
                fd.field('Lookup').value = 5;

                //MULTI CHOICE LOOKUP

                //returns an array of the selected IDs
                fd.field('LookupMulti').value;

                //returns an ID of the first selected
                fd.field('LookupMulti').value[0];

                // returns first selected element as text:
                fd.field('LookupMulti').value[0].LookupValue; 

                //set with an array of IDs:
                fd.field('LookupMulti').value = ["2", "3", "4"];

                //alerts all values as a string of IDs
                var selected = fd.field('LookupMulti').value;
                var s = '';
                for (var i = 0; i < selected.length; i++) {
                    s += selected[i].ID + '; ';
                }
                alert(s);

                //alerts all values as a text string
                var selected = fd.field('LookupMulti').value;
                var s = '';
                for (var i = 0; i < selected.length; i++) {
                    s += selected[i].LookupValue + '; ';
                }
                alert(s);

    *   -   **ready**
        -   Returns promise that is resolved when the field has fully loaded. Useful for executing scripts as soon as the field fully loads.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').ready().then(function(field) {
                    console.log(field.value.LookupValue);
                });

    *   -   **addNewText**
        -   Get or set text for adding new element, useful for localization. Appears if search is unsuccessful.

            Must be set before the field is rendered.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spBeforeRender(function() {
                    fd.field('Lookup').addNewText = "Ajouter un nouvel élément";
                });
                

    *   -   **noDataText**
        -   Get or set text when no items are found, useful for localization. Appears if search is unsuccessful.

            Must be set before the field is rendered.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spBeforeRender(function() {
                    fd.field('Lookup').noDataText = 
                        "Не найдено. Добавить элемент - '#: instance.filterInput.val() #'?";
                });
                

    *   -   **title**
        -   Get or set the title of the field.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').title;
                fd.field('Lookup').title = "Super Lookup";
    
    *   -   **operator**
        -   Get or set search operator. Can search for elements that either start with entered text or contain it.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').operator;
                fd.field('Lookup').operator = "startsWith";
                fd.field('Lookup').operator = "contains";
                
    *   -   **orderBy**
        -   Set $orderby Query Option. Allows to sort the results by one or multiple fields.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').orderBy = 'Title';
                fd.field('Lookup').orderBy = { field: 'Title', desc: true };
                fd.field('Lookup').operator = [
                    { field: 'FirstChoice', desc: true },
                    { field: 'Title', desc: false }
                ];

    *   -   **disabled**
        -   Check if field is disabled, or set field to disabled or editable state.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').disabled;
                fd.field('Lookup').disabled = true;
                fd.field('Lookup').disabled = false;

    *   -   **readonly**
        -   Check if field is readonly. Cannot be changed.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').readonly;

    *   -   **extraFields**
        -   Get or set Extra Fields to retrieve from the source list. Returns an array.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').extraFields;
                fd.field('Lookup').extraFields = ["Category/Id", "Category/Title"];

    *   -   **expandFields**
        -   Get or set Expand Fields (need for all Lookups) to retrieve extra data. Returns an array.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').extraFields;
                fd.field('Lookup').extraFields = ["Category"];
        
    *   -   **filter**
        -   Get or set filter query for the lookup, which will filter the results. 
        
            Read more about OData $filter query |OData Filter|. 
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').filter;
                fd.field('Lookup').filter = "Country eq '" + fd.field("Country").value + "'";

    *   -   **widget**
        -   Returns jquery-object lying under the Vue-component. 
        
            For Single choice Lookup it is |LookupKendo| widget. 
            
            For Multiple Choice Lookup it is |LookupKendoMulti| widget.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('Lookup').widget;

    *   -   **widgetOptions**
        -   Get or set configuration options for the lookup. Must be set before the fields render, cannot be changed afterwards.
        
            Read more about Single Choice Lookup configuration |OptionsLookupSingle|. 
            
            Multiple Choice Lookup configuration |OptionsLookupMultiple|.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spBeforeRender(function() {
                    //display Extra Field Price, if it is available 
                    var tmp = '#: data.LookupValue # #: data.Price ? " $" + data.Price : "" #';
                    fd.field('Lookup').widgetOptions = {
                        template: tmp,
                        valueTemplate: tmp
                    }
                });

    *   -   **dialogOptions**
        -   |Kendo UI Window| configuration. 
        
            Holds dialog window options when adding new items, such as width and height.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.control('SPDataTable0').dialogOptions.height; //returns height
                fd.control('SPDataTable0').dialogOptions.width //returns width

                //set width and height:
                fd.control('SPDataTable0').dialogOptions = {
                    width: 1280,
                    height: 720
                }
    *   -   **$on('change')**
        -   Triggers on 'change' event.

            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Lookup').$on('change', function(value) {
                    alert('New value: ' + value.LookupValue));
                });


.. |Kendo UI Window| raw:: html

    <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/window#configuration" target="_blank">Kendo UI Window</a>

.. |LookupKendo| raw:: html

   <a href="https://demos.telerik.com/kendo-ui/dropdownlist/index" target="_blank">DropDownList</a>

.. |LookupKendoMulti| raw:: html

   <a href="https://demos.telerik.com/kendo-ui/multiselect/index" target="_blank">MultiSelect</a>

.. |OptionsLookupSingle| raw:: html

   <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/dropdownlist" target="_blank">here</a>

.. |OptionsLookupMultiple| raw:: html

   <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/multiselect" target="_blank">here</a>

.. |OData Filter| raw:: html

   <a href="https://docs.microsoft.com/en-us/sharepoint/dev/sp-add-ins/use-odata-query-operations-in-sharepoint-rest-requests" target="_blank">here</a>


Boolean - Yes/No
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns true or false:
                fd.field('Boolean').value; 

                // can set with true/false:
                fd.field('Boolean').value = false;

                // can set with 0/1:
                fd.field('Boolean').value = 1; 

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Boolean').$on('change', function(value) {
                    alert('New value: ' + value);
                });

People Picker
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                //returns an array of objects
                fd.field('Persons').value;

                //returns email of the first selected user
                fd.field('Persons').value[0].EntityData.Email;

                //returns display name of the first selected user
                fd.field('Persons').value[0].DisplayText

                // assign value by a display name
                fd.field('Persons').value = "John Smith";

                // or by an e-mail:
                fd.field('Persons').value = "john.smith@mail.com";
    
    *   -   **ready**
        -   Returns promise that is resolved when the field has fully loaded. Useful for executing scripts as soon as the field fully loads.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //will run once the field is initialized
                //returns all names as a string
                fd.field('Persons').ready().then(function(field) {
                    var people = field.value;
                    var s = '';
                    for (var i = 0; i < people.length; i++) {
                        s += people[i].DisplayText + '; ';
                    }
                    alert(s);
                });


    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Persons').$on('change', function(value) {
                    var people = value;
                    var s = '';
                    for (var i = 0; i < people.length; i++) {
                        s += people[i].DisplayText + '; ';
                    }
                    alert('New value: ' + s);
                });

Managed Metadata (Taxonomy) Single
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns an object
                fd.field('Taxonomy').value;

                // returns the name of the selected option
                fd.field('Taxonomy').value.Name; 

                // returns the ID of the selected option
                fd.field('Taxonomy').value.Id; 

                //set element with the an object:
                fd.field('Taxonomy').value = { 
                    Id: "ac68fff3-2826-48f1-8d24-3fadad9533f0", 
                    Name: "Test1"
                };

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('Taxonomy').$on('change', function(value) {
                    alert('New value: ' + value.Name);
                });

Managed Metadata (Taxonomy) Multiple
--------------------------------------------------


.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples

    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                // returns an array of objects
                fd.field('TaxonomyMulti').value;

                // returns the name of the first selected option
                fd.field('TaxonomyMulti').value[0].Name; 

                // returns the ID of the first selected option
                fd.field('TaxonomyMulti').value[0].Id; 

                //returns all selected options as a text string
                var terms = fd.field('TaxonomyMulti').value;
                var s = '';
                for (var i = 0; i < terms.length; i++) {
                    s += terms[i].Name + '; ';
                }
                alert(s);

                //set element with the an array:
                fd.field('TaxonomyMulti').value = [{ 
                    Id: "ac68fff3-2826-48f1-8d24-3fadad9533f0", 
                    Name: "Term1"
                },
                {
                    Id: "53e1c22e-bfc4-4172-81ff-806415606837",
                    Name: "Term2"
                }];

    *   -   **$on('change')**
        -   Triggers on 'change' event.

           
            
            |

            *Example:*

            .. code-block:: javascript

                fd.field('TaxonomyMulti').$on('change', function(value) {
                    var terms = value;
                    var s = '';
                    for (var i = 0; i < terms.length; i++) {
                        s += terms[i].Name + '; ';
                    }
                    alert('New value: ' + s);
                });

Content Type
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **value**
        -   Allows to get or set selected value. 
            
            |

            *Examples:*
            
            .. code-block:: javascript

                //returns string with Content Type ID
                fd.field('ContentType').value;

                //will redirect to the page with the form for the Content Type:
                fd.field('ContentType').value = "0x0100EF07682335C8DD4BBF2D7D82C74F52D1"

    *   -   **ready**
        -   Returns promise that is resolved when the field has fully loaded. Useful for executing scripts as soon as the field fully loads.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('ContentType').ready().then(function(field) {
                    console.log(field.value);
                    // or
                    console.log(fd.field('ContentType').value);
                });