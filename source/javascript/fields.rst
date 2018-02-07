Fields
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Intro
--------------------------------------------------
Here you can find properties of the fields that you have on your form and methods that can be used on them. 

Insert them into JavaScript editor or inside OnClick setting for buttons and links.

*Internal Name* is the property that is used to identify specific fields and apply methods to them. *Internal Name* is unique for every element on the form.

**Important!** These events, methods and properties shouldn't be used on their own, they must be executed inside events 
like **rendered()** or **beforeSave()** in order to actually access the fields or controls that you target.

If you just add these scripts on their own or inside wrong event in JavaScript editor,
they will not have access to the specified fields, or will execute at the wrong time.
Read more about different events in :doc:`Manager section </javascript/manager>`.

For more use cases, check out :doc:`our manual </how-to/conditional-fields>` on how-to adjust fields dynamically on your form.

Properties
--------------------------------------------------
Most fields have these properties:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20

    *   -   Property
        -   Description
        -   Examples
    *   -   **disabled**
        -   Returns true if the field is disabled, allows to disable a field, making it essentially Read-only.
        - .. code-block:: javascript

                fd.field('TextBox').disabled;
                fd.field('TextBox').disabled = true;
    
    *   -   **placeholder**
        -   Get or set placeholder for a field.

            Only works for fields that have Placeholder property.
        - .. code-block:: javascript

                fd.field('TextBox').placeholder;
                fd.field('TextBox').placeholder = 'Confirm Password';

    *   -   **required**
        -   Returns true if the field is required. 
        
            For SharePoint fields only adds or removes asterisk near the title. 
            
            For Plumsail fields it also adds validation.

        - .. code-block:: javascript
                
                fd.field('TextBox').required;
                fd.field('TextBox').required = true;
                fd.field('TextBox').required = false;

    *   -   **title**
        -   Allows to get or set field's title.
        - .. code-block:: javascript

                fd.field('TextBox').title;
                fd.field('TextBox').title = 'New Title';

    *   -   **validators**
        -   Returns an array of field validators, can be used to add new ones.

            These include simple validators for one field, that only check if specific field matches certain criteria or not.

            If the field does not match the criteria, the form will not submit.

            *Note: Field validators will only work with Plumsail fields as all validation for SharePoint fields is configured via List Settings.*

            Use **rendered()** event for Plumsail forms and **spRendered()** event for SharePoint forms to add custom validators.
        - .. code-block:: javascript

                fd.field('Numeric').validators;
        
                fd.field('Numeric').validators.push({
                    name: 'MyCustomValidator',
                    error: '',
                    validate: function(value) {
                        if (value <= 0) {
                            this.error = 'Value must by greater than 0';
                            return false;
                        }
                        
                        if (value > 2000) {
                            this.error = 'Value must be less than 2000';
                            return false;
                        }
                        
                        return true;
                    }
                });

    *   -   **value**
        -   Allows to get or set field's value.

            *Plumsail fields* and their value types:

            * TextBox, MultilineTextBox, DropDown, Radios – string

            * Checkboxes, DropDown(multiple) – array of strings

            * Date, DateTime – Date

            * Numeric – number
        - .. code-block:: javascript

                fd.field('TextBox').value;
                fd.field('TextBox').value = 'Hello, world!';
                fd.field('Checkboxes').value = ['Choice1', 'Choice2'];
                fd.field('Date').value = new Date();
                fd.field('Numeric').value = 100;

    *   -   **widget**
        -   Returns jquery-object lying under the Vue-component. 
        
            Usually it's a kendo component.
        - .. code-block:: javascript

                fd.field('TextBox').widget;

Methods
--------------------------------------------------
These methods are applicable to most fields:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Method
        -   Description
        -   Examples
    
    *   -   **clear()**
        -   Clears the field.
        - .. code-block:: javascript

                fd.field('TextBox').clear();

    *   -   **validate()**
        -   Checks to see if field is valid or not. If not, returns false, highlights field and adds error message under it.
        - .. code-block:: javascript

                fd.field("TextBox").validate();

Events
--------------------------------------------------
Fields use **$on()** method to track the events happening to them. 

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Event
        -   Description
        -   Examples

    *   -   **change**
        -   Triggers when field value is changed.
        - .. code-block:: javascript

                fd.field('TextBox').$on('change', function(value) {
                    alert('New value: ' + value);
                });
    *   -   **ready**
        -   Triggers when the field is initialized and is ready to be used in scripts. **Only available for People picker and Content Type SharePoint fields!**
        - .. code-block:: javascript

                fd.spRendered(function() {
                    fd.field('User').$on('ready',function(field) {
                        console.log(field.value);
                        // or
                        console.log(fd.field('User').value);
                    });

                    fd.field('ContentType').$on('ready',function(field) {
                        console.log(field.value);
                        // or
                        console.log(fd.field('ContentType').value);
                    });
                });