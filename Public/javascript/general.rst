.. title:: Intro to JS framework of Plumsail Forms (public forms)

.. meta::
   :description: General information and JavaScript API variables

Introduction to JavaScript framework of Plumsail Forms (public forms)
====================================================================================================

Limitless possibilities
--------------------------------------------------
Modern Forms are highly customizable and it's JavaScript which allows you to go above and beyond any limitations you might face.

Bootstrap and custom styles can make your form look great on any screen and device, but JavaScript can add often much needed interactivity to the form.

Modern Forms are built with Vue.js and also support JQuery.

    - You can find general information about JavaScripts used on the form in the :doc:`Manager section </javascript/manager>`.

    - :doc:`Containers </javascript/containers>`, :doc:`Controls </javascript/controls>`, :doc:`Fields </javascript/fields>` sections provide detailed explaination of JS properties, methods and events for these elements.

    - Finally, check out our How-to section for practical examples of JavaScript use, 
      such as :doc:`Manipulate fields </how-to/conditional-containers>` 
      and :doc:`Manipulate containers </how-to/conditional-containers>` articles.

Available framework variables
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Variable
        -   Description/Examples
        
    *   -   **fd**
        -   :doc:`JavaScript manager </javascript/manager>` used in most operations with the form. Allows access to all events, controls, fields, validators and data on the form.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //make fd available in browser's console
                window.fd = fd;

                //call form rendered event
                fd.rendered(function() {
                    //fields are available to get/set
                    fd.field('Title').value = "New Title";
                });

    *   -   **$**
        -   |jQuery library| which can be used for a variety of things, to apply styles dynamically to the form, hide and show fields and much more.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //make jQuery available in browser's console
                window.$ = $;

                //hide fields with CSS class
                $('.field-to-hide').css('visibility', 'hidden');

                //make fields with CSS class visible
                $('.field-to-hide').css('visibility', 'visible');

.. |jQuery library| raw:: html	

    <a href="https://jquery.com" target="_blank">jQuery library</a>