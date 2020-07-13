.. title:: Managing form with JS in Plumsail Forms (public forms)

.. meta::
   :description: JavaScript API for managing the form

Managing form with JavaScript in Plumsail Forms (public forms)
=============================================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Introduction
--------------------------------------------------
**fd** is a Forms designer manager variable. Whenever you want to use custom methods on the form, you need to call the manager first. 

 **fd** is not global and only accesible from within the form, e.g. from JavaScript editor. 

 It is accesible globally in Form Preview, so you can run tests from browser's console.

 Otherwise, it will not be accesible globally on the page, so you can include several forms on one page and not worry about their scripts conflicting at all.

Properties
--------------------------------------------------
**fd** has the following properties:

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples

    *   -   **fd.culture**

        -   Returns the name of the current culture.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.culture; //"en-US"

    *   -   **fd.formId**
        -   Returns ID of the form.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.formId; //"b5257750-2483-4bea-ac1a-79ad7c670756"

    *   -   **fd.isFilesUploadingInProgress**

        -   Returns *true* if files are currently uploaded as attachments, returns *false* otherwise.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.isFilesUploadingInProgress;

    *   -   **fd.isValid**

        -   Checks if form is valid or not. 
            
            Each time the property is called, it runs a method to check if all validators validate succesfully, both Field and Form validators.

            Returns *true* on success. Otherwise, returns *false* and error messages get displayed.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.isValid;

    *   -   **fd.validators**
    
        -   Get an array of form validators, can be used to add new ones.
            These are more complex validators than Field Validators and are used for several fields, to check that different fields have appropriate values.

            For example, you want certain options to be only available if the user's age is above 18 or some other criteria.

            If the fields do not match these criterias, the form will not submit.

            Use **rendered()** event to add custom validators.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.validators;

                fd.validators.push({
                    name: 'MyCustomValidator',
                    error: "Age must be 18 or over in order to subscribe",
                    validate: function(value) {
                        if (fd.field('Age').value < 18 
                        && fd.field('PaymentModel').value == 'Subscription')
                            return false;
                            
                        return true;
                    }
                });

    *   -   **fd._vue**

        -   Get **VueJS** component of the form, so you can examine or modify it.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd._vue;

    *   -   **fd.messages**

        -   Property that stores all language constants, can be used to set text for localization.

            *It's best to use* **created** *event to set these values.*
            
            |

            *Example:*
            
            .. code-block:: javascript

                //example of setting language constant in created event
                fd.created(function(vue) {
                    fd.messages.PlumsailForm_Submission_Success = 'Thank you!';
                });

                //All default values:
                fd.messages.Failure_General = 
                    "An error has occured. Please check the browser console (F12).";

                fd.messages.Failure_ItemNotFound = 
                    "An item was not found. It may have been deleted or renamed by another user.";

                fd.messages.PlumsailForm_CorrectErrors = 
                    "Please correct the errors below:";

                fd.messages.PlumsailForm_Submission_Error = 
                    "An error has occured while saving the form. Please check the console (F12).";

                fd.messages.PlumsailForm_Submission_Success = 
                    "The form has been submitted successfully.";

                fd.messages.RequiredValidator_Error = 
                    "This field is required.";


Methods
--------------------------------------------------
These methods can be applied to **fd**:

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Method
        -   Description/Examples
    *   -   **fd.save()**
        -   Saves the form.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.save();
                
    *   -   **fd.data()**
        -   Gathers data from all fields on the form. Can be used to get or set multiple values at the same time.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.data();
                fd.data({Field1: value1, Field2: value2});

    *   -   **fd.clear()**
        -   Clears the form.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.clear();

    *   -   **fd.exportToPDF(fileName, options)**
        -   Exports current form to PDF file, and starts file download.

            **fileName** passed as an argument to the function is a string with the name of the created file.

            **options** passed as an argument to the function is a JavaScript object that specifies various options for created PDF file, such as paper size, margin, orientation, etc.

            Find more about |PDF options|.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.exportToPDF('contacts-form', {
                    paperSize: 'A4',
                    landscape: false,
                    multiPage: true
                });

.. _js-events:

Events
--------------------------------------------------
These events can be executed from JavaScript editor for Plumsail Forms:

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Event
        -   Description/Examples
    *   -   **beforeCreate()**
        -   Occurs prior to form creation.
        
            **vueConfig** passed as an argument to the function is a configuration of the main vue-component. You can register your own child components.
            You can read more about it |vueConfig|.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.beforeCreate(function(vueConfig) {
                    console.log('beforeCreate');
                    console.log(vueConfig);
                });

    *   -   **created()**
        -   Occurs as soon as the form is created.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.created(function(vue) {
                    console.log('created');
                    console.log(vue);
                });

    *   -   **beforeRender()**
        -   Occurs before mounting the vue-component to DOM.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.beforeRender(function(vue) {
                    console.log('beforeRender');
                    console.log(vue);
                });

    *   -   **rendered()**
        -   Occurs after mounting the vue-component to DOM.

            **Best place to run your JavaScript** since all elements are already built and rendered.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.rendered(function(vue) {
                    console.log('rendered');
                    console.log(vue);
                });

                fd.rendered(function(){
                    fd.validators.push({
                        name: 'MyCustomValidator',
                        error: '"To" must be greater or the same as "From".',
                        validate: function(value) {
                            if (fd.field('From').value >= fd.field('To').value)
                                return false;
                                
                            return true;
                        }
                    });
                });

    *   - **beforeSave()**
        -   Occurs before submitting the form.

            **data** passed as an argument to the function is an object representing user's input. 
            
            Keys are internal names of form fields, Values - user's input. Ex.:

            .. code-block:: javascript

                {
                    Field1: 'text'
                    DateTime1: new Date('2017-01-01')
                }

            Here, you can process form's data with code by yourself instead of sending it to the Flow. 
            
            For instance, you can send data directly to your web service or modify it somehow before it is processed by the Flow.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

            |

            *Examples:*
            
            .. code-block:: javascript

                fd.beforeSave(function(data) {
                    console.log('beforeSave');
                    console.log(data);
                });

            Asynchronous:

            .. code-block:: javascript

                fd.beforeSave(function(data) {
                return new Promise(function(resolve) {
                        // loading extra data from external data sources
                        $.getJSON('https://mywebservice.contoso.com')
                            .then(function(result) {
                                data.additionalProperties = result;
                                resolve();
                            })
                    }); 
                });

    *   -   **saved()**
        -   Occurs after the data is sent to the Flow.

            Can be used to display confirmation message after the form is saved or perform some other actions.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.saved(function() {
                    console.log('saved');
                });
    
    
.. |vueConfig| raw:: html

    <a href="https://vuejs.org/v2/guide/instance.html" target="_blank">here</a>

.. |PDF options| raw:: html	

    <a href="https://docs.telerik.com/kendo-ui/framework/drawing/pdf-output#configuration-PDF" target="_blank">PDF options here</a>