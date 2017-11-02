Methods
==================================================

Fields
--------------------------------------------------

General methods
**************************************************
These methods are applicable to most fields:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Method
        -   Description
        -   Examples
    *   -   **field(FieldName).title**
        -   Allows to get or set field's title.
        - .. code-block:: javascript

                fd.field('TextBox').title;
                fd.field('TextBox').title = "New Title";

    *   -   **field(FieldName).required**
        -   Returns true if the field is required. 
        
            For SharePoint fields only adds or removes asterisk near the title. 
            
            For Plumsail fields it also adds validation.

        - .. code-block:: javascript
                
                fd.field('TextBox').required;
                fd.field('TextBox').required = true;
                fd.field('TextBox').required = false;

    *   -   **field(FieldName).value**
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

    *   -   **field(FieldName).disabled**
        -   Returns true if the field is disabled, allows to disable a field, making it essentially Read-only.
        - .. code-block:: javascript

                fd.field('TextBox').disabled;
                fd.field('TextBox').disabled = true;
    *   -   **field(FieldName).clear**
        -   Clears the field.
        - .. code-block:: javascript

                fd.field('TextBox').clear();

    *   -   **field(FieldName).placeholder**
        -   Get or set placeholder for a field.

            Only works for fields that have Placeholder property.
        - .. code-block:: javascript

                fd.field('TextBox').placeholder;
                fd.field('TextBox').placeholder = 'Confirm Password';

    *   -   **field(FieldName).widget**
        -   Returns jquery-object lying under the Vue-component. 
        
            Usually it's a |kendo-widget|.
        - .. code-block:: javascript

                fd.field('TextBox').widget;

    *   -   **field(FieldName).$on**
        -   Tracks when specific events happens to a field. 
            
            By default only has **change** event which triggers when field value is changed.
        - .. code-block:: javascript

                fd.field('TextBox').$on('change', function(value) {
                    alert('New value: ' + value);
                })



.. |kendo-widget| raw:: html

    <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/widget" target="_blank">Kendo Widget</a>