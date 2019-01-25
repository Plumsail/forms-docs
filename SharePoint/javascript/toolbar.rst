Toolbar
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Intro
--------------------------------------------------
**fd.toolbar** can be used to customize form's toolbar.

Properties
--------------------------------------------------

.. list-table::
    :widths: 10 30

    *   -   **fd.toolbar**

        -   Property that holds all the parameters for the toolbar.                

    *   -   **fd.toolbar.buttons**

        -   Property that holds all available buttons in an array of objects.

            Can be used to add new buttons, modify or remove existing ones.

            Buttons have the following properties:

            **class** - returns an object, holds button's CSS classes. Can be used to assign CSS classes with either string or an object. 
            Default class *btn* cannot be removed or changed, is not contained in the property.

            **click** - returns a function, that is executed when a button is clicked. Can be used to assign a new function.

            **disabled** - return boolean, whether button is disabled or not. Can be used to disable or enable a button.

            **icon** - returns a string, which matches icon names from |Microsoft Fabric Icons|. Can be used to add or change button's icon.

            **style** - returns a string, which matches button's HTML property style. Can be used to add styles to a specific button.

            **text** - returns a string, which matches button's text. Can be used to retrieve or change button's text.
            
            |

            *Example:*
            
            .. code-block:: javascript
                
                fd.spRendered(function(){ 
                    //set button's class
                    fd.toolbar.buttons[1].class  = 'btn-danger';
                    //or
                    fd.toolbar.buttons[1].class  = {'btn-danger': true};

                    //change click function
                    fd.toolbar.buttons[1].click = function(){
                        if (confirm('Are you sure you want to exit the form?')) {
                            fd.close();
                        } 
                    }

                    //disable save button
                    fd.toolbar.buttons[0].disabled = true;

                    //set button's icon
                    fd.toolbar.buttons[0].icon = "Save";

                    //set button's style (hide a button)
                    fd.toolbar.buttons[0].style = "display: none;";

                    //set button's text
                    fd.toolbar.buttons[0].text = "Submit";
                    
                    //add new button
                    fd.toolbar.buttons.push({
                        icon: 'Flow',
                        class: 'btn-outline-primary',
                        text: 'Send for approval',
                        click: function() {
                            alert('Clicked!');
                        }
                    });
                });

.. |Microsoft Fabric Icons| raw:: html

    <a href="https://developer.microsoft.com/en-us/fabric#/styles/icons" target="_blank">Microsoft Fabric Icons</a>