Fields
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Intro
--------------------------------------------------
Here you can find properties of Common fields that you have on your form and methods that can be used on them. 

Insert them into JavaScript editor or inside OnClick setting for buttons and links.

*Internal Name* is the property that is used to identify specific fields and apply methods to them. *Internal Name* is unique for every element on the form.

.. important::  These events, methods and properties shouldn't be used on their own, they must be executed inside events 
                like **spRendered()** or **spBeforeSave()** in order to actually access the fields or controls that you target.

                If you just add these scripts on their own or inside wrong event in JavaScript editor,
                they will not have access to the specified fields, or will execute at the wrong time.
                Read more about different events in :doc:`Manager section </javascript/manager>`.

For more use cases, check out :doc:`our manual </how-to/conditional-fields>` on how-to adjust fields dynamically on your form.

Properties
--------------------------------------------------
Most fields have these properties:

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
    *   -   **disabled**
        -   Returns true if the field is disabled, allows to disable a field, making it essentially Read-only.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.field('TextBox').disabled;
                fd.field('TextBox').disabled = true;
    
    *   -   **placeholder**
        -   Get or set placeholder for a field.

            Only works for fields that have Placeholder property.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.field('TextBox').placeholder;
                fd.field('TextBox').placeholder = 'Confirm Password';

    *   -   **required**
        -   Returns true if the field is required. 
        
            For SharePoint fields only adds or removes asterisk near the title. 
            
            For Plumsail fields it also adds validation.
            
            |

            *Examples:*
            
            .. code-block:: javascript
                
                fd.field('TextBox').required;
                fd.field('TextBox').required = true;
                fd.field('TextBox').required = false;

    *   -   **title**
        -   Allows to get or set field's title.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.field('TextBox').title;
                fd.field('TextBox').title = 'New Title';

    *   -   **validators**
        -   Returns an array of field validators, can be used to add new ones.

            These include simple validators for one field, that only check if specific field matches certain criteria or not.

            If the field does not match the criteria, the form will not submit.

            Use **rendered()** event for Plumsail forms and **spRendered()** event for SharePoint forms to add custom validators.
            
            |

            *Examples:*
            
            .. code-block:: javascript

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
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.field('TextBox').value;
                fd.field('TextBox').value = 'Hello, world!';
                fd.field('Checkboxes').value = ['Choice1', 'Choice2'];
                fd.field('Date').value = new Date();
                fd.field('Numeric').value = 100;

    *   -   **widget**
        -   Returns jquery-object lying under the Vue-component. 
        
            Usually it's a kendo component.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('TextBox').widget;

MaskedTextBox Unique Properties
--------------------------------------------------
These properties are only applicable to MaskedTextBox field:

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **mask**
        -   Property that holds the Mask for the MaskedTextBox field, can be used to get it or set it.

            The following mask rules are supported:

            0 - Digit. Accepts any digit between 0 and 9.

            9 - Digit or space. Accepts any digit between 0 and 9, plus space.

            # - Digit or space. Like 9 rule, but allows also (+) and (-) signs.

            L - Letter. Restricts input to letters a-z and A-Z. This rule is equivalent to [a-zA-Z] in regular expressions.

            ? - Letter or space. Restricts input to letters a-z and A-Z. This rule is equivalent to [a-zA-Z] in regular expressions.

            & - Character. Accepts any character. The rule is equivalent to \S in regular expressions.

            C - Character or space. Accepts any character. The rule is equivalent to . in regular expressions.

            A - Alphanumeric. Accepts letters and digits only.

            a - Alphanumeric or space. Accepts letters, digits and space only.

            . - Decimal placeholder. The decimal separator will be gotten from the current culture.

            , - Thousands placeholder. The display character will be gotten from the current culture.

            $ - Currency symbol. The display character will be gotten from the current culture.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('MaskedTextBox0').mask;
                fd.field('MaskedTextBox0').mask = "(999) 000-0000";

            For more examples, please, checkout |KendoUI MaskedTextBox|.

.. |KendoUI MaskedTextBox| raw:: html

               <a href="https://demos.telerik.com/kendo-ui/maskedtextbox/index" target="_blank">KendoUI MaskedTextBox</a>

MultilineTextBox Unique Properties
--------------------------------------------------
These properties are only applicable to MultilineTextBox field:

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
    
    *   -   **widgetOptions**
        -   The property contains settings for |Kendo UI MultilineTextBox control|. 
        
            Customize the collection of tools that are used to interact with the text.

            Tools may be switched on by specifying their names. 

            The available editor commands are:

            **Basic text formatting**:

            'bold', 'italic', 'underline', 'strikethrough', 'subscript', 'superscript'
            

            **Font and color**:

            'fontName', 'fontSize', 'foreColor', 'backColor'


            **Alignment**:

            'justifyLeft', 'justifyCenter', 'justifyRight', 'justifyFull' 


            **Lists**:

            'insertUnorderedList', 'insertOrderedList', 'indent', 'outdent' 


            **Links, images and files**:

            'createLink', 'unlink', 'insertImage', 'insertFile' 


            **Table editing**:

            'tableWizard', 'createTable', 'addColumnLeft', 'addColumnRight', 
            'addRowAbove', 'addRowBelow', 'deleteRow', 'deleteColumn' 


            **Structural markup and styles**:

            'formatting',  'cleanFormatting'  

            
            **HTML code view**:

            'viewHtml'


            **Print edited field**:  

            'print'


            **Custom**:
            
            Add a custom button to the tools pane which will run the JavaScript function. 

            
            *Example:*
            
            .. code-block:: javascript
                
                fd.spRendered(function() {
                    fd.field('MultilineTextBox0').widgetOptions = {
                        tools: [
                            { name: 'italic' },
                            { name: 'underline' },
                            { name: 'justifyLeft' },
                            { name: 'justifyCenter' },
                            { name: 'justifyRight' }, 
                            {
                                name: "custom",
                                tooltip: "Insert profile template",
                                exec: function(e) {
                                    var editor = $(this).data("kendoEditor");
                                    editor.exec("inserthtml", { 
                                        value: "<strong>Name: </strong><br />
                                                <strong>Age: </strong><br /> 
                                                <strong>Gender: </strong><br />
                                                <strong>Email: </strong><br />" 
                                    });
                                }
                            }
                        ]
                    } 
                });   
.. |Kendo UI MultilineTextBox control| raw:: html

               <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/editor/configuration/tools" target="_blank">Kendo UI MultilineTextBox control</a>


                 
Numeric Field Unique Properties
--------------------------------------------------
These properties are only applicable to Numeric field: 

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples
        
    *   -   **widgetOptions**
        -   The property contains settings for |Kendo UI NumericTextBox control|. 

            - **decimals** - Specifies the number of precision applied to the field value. If not set, the precision defined by the current culture is used.

            - **factor** - Specifies the factor by which the value is multiplied. 

            - **format** - Specifies displayed number format.

              - "n", "n0", "n3" — Renders a number.

              - "c", "c0", "c3" — Renders a currency value.
              
              - "p", "p0", "p3" — Renders a percentage (number is multiplied by 100).

                Where 0,3 - number of decimal places displayed.

            - **min** / **max** - Specifies the largest and smallest value the user can enter. 

            - **restrictDecimals** - Specifies whether the length of the decimal should be restricted during typing. The length of the fraction is defined by the decimals value.  

            - **round** - Specifies whether the value should be rounded or truncated. 

            - **step** - Specifies the value used to increment or decrement widget value. 

            |

            *Example #1*

            Input value: **153.965**

            Displayed value: **$154**
            
            .. code-block:: javascript

                fd.field('Numeric0').widgetOptions = {
                    format:"c0",
                    decimals: 3
                }
            
            |

            *Example #2*

            Input value: **95**

            Displayed value: **95%**

            Value increments/decrements by one.
            
            .. code-block:: javascript

                fd.field('Numeric0').widgetOptions = {
                    format: "p0",
                    factor: 100,
                    min: 0,
                    max: 1,
                    step: 0.01
                }

            |

            *Example #3*

            Input value: **122,7669**

            Displayed value: **122,77**
            
            .. code-block:: javascript

                fd.field('Numeric0').widgetOptions = {
                    format: "n2",
                    decimals: 4
                }                         
.. |Kendo UI NumericTextBox control| raw:: html

               <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/numerictextbox" target="_blank">Kendo UI NumericTextBox control</a>



Methods
--------------------------------------------------
These methods are applicable to most fields:

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Method
        -   Description/Examples
    
    *   -   **clear()**
        -   Clears the field.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('TextBox').clear();

    *   -   **validate()**
        -   Checks to see if field is valid or not. If not, returns false, highlights field and adds error message under it.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field("TextBox").validate();

Events
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Event
        -   Description/Examples

    *   -   **change**
        -   Triggers when field value is changed.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.field('TextBox').$on('change', function(value) {
                    alert('New value: ' + value);
                });
    *   -   **ready**
        -   Returns promise that is resolved when the field has fully loaded. Useful for executing scripts as soon as the field fully loads.
        
            **Only available for List or Library control, People picker, Lookup and Content Type SharePoint fields!**
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spRendered(function() {
                    fd.field('User').ready().then(function(field) {
                        console.log(field.value);
                        // or
                        console.log(fd.field('User').value);
                    });

                    fd.field('ContentType').ready().then(function(field) {
                        console.log(field.value);
                        // or
                        console.log(fd.field('ContentType').value);
                    });
                });