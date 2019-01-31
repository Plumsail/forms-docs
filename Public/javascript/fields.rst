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
        
            Allows setting fields to be required.
            
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