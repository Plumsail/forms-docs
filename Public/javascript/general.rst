JavaScript Intro
==================================================

Limitless possibilities
--------------------------------------------------
Modern Forms are highly customizable and it's JavaScript which allows you to go above and beyond any limitations you might face.

Bootstrap and custom styles can make your form look great on any screen and device, but JavaScript can add often much needed interactivity to the form.

Modern Forms are built with Vue.js and comes with JQuery. On SharePoint forms, pnp-js library can be used to additional data from SharePoint.

    - You can find general information about JavaScripts used on the form in the :doc:`Manager section </javascript/manager>`.

    - :doc:`Containers </javascript/containers>`, :doc:`Controls </javascript/controls>`, :doc:`Fields </javascript/fields>`, 
      and :doc:`SharePoint Fields </javascript/fields-sp>` sections provide detailed explaination of JS properties, methods and events for these elements.

    - Finally, check out our How-to section for practical examples of JavaScript use, 
      such as :doc:`Manipulate fields </how-to/conditional-containers>` 
      and :doc:`Manipulate containers </how-to/conditional-containers>` articles.

Available framework variables
--------------------------------------------------

Common variables (SharePoint and Public)
**************************************************

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

                //call SharePoint form rendered event
                fd.spRendered(function() {
                    //simple fields are available
                    fd.field('Title').value = "New Title";

                    //can use ready event for complex fields
                    fd.field('Lookup').ready().then(function(field) {
                        console.log(field.value.LookupValue);
                    });
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

SharePoint variables
**************************************************

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Variable
        -   Description/Examples

    *   -   **Dialog**
        -   :doc:`Dialog </javascript/dialog>` can be used to open any other form in dialog, pass parameters to it, detect if it was saved or not, and pass parameters back.
        
            |

            *Example:*
            
            .. code-block:: javascript

                //make Dialog available in browser's console
                window.Dialog = Dialog;

                //open form in dialog
                Dialog.open('{Form URL}', { args: 'something' });

    *   -   **pnp**
        -   |pnpjs library| for SharePoint REST services (within current site).
            
            |

            *Example:*
            
            .. code-block:: javascript

                //make pnp-js available in browser's console
                window.pnp = pnp;

                //get current Web:
                var web = pnp.sp.web;

                //get current Site:
                var site = pnp.sp.Site;

    *   -   **Web**
        -   Allows to create |Web| instances directly using with the URL to use as a base.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //make Web available in browser's console
                window.Web = Web;

    *   -   **Site**
        -   Allows to create Site instances directly using with the URL to use as a base.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //make Site available in browser's console
                window.Site = Site;
    

.. |jQuery library| raw:: html

    <a href="https://jquery.com" target="_blank">jQuery library</a>


.. |pnpjs library| raw:: html

    <a href="https://github.com/pnp/pnpjs/blob/dev/packages/sp/docs/index.md" target="_blank">pnpjs library</a>

.. |Web| raw:: html

    <a href="https://pnp.github.io/pnpjs/documentation/getting-started/#create-web-instances-directly" target="_blank">Web</a>