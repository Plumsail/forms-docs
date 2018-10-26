Manager
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Intro
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

            Use **rendered()** event for Plumsail forms and **spRendered()** event for SharePoint forms to add custom validators.
            
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

    *   -   **fd._vue.lang**

        -   Property that stores all language constants, can be used to set text for localization.

            It's best to use **created** event to set these values;
            
            |

            *Example:*
            
            .. code-block:: javascript

                //example of setting language constant in created event
                fd.created(function(vue) {
                    vue.lang.PlumsailForm_Submission_Success = 'Thank you!';
                });

                //All default values:
                fd._vue.lang.Failure_General = 
                    "An error has occured. Please check the browser console (F12).";

                fd._vue.lang.Failure_ItemNotFound = 
                    "An item was not found. It may have been deleted or renamed by another user.";

                fd._vue.lang.PlumsailForm_CorrectErrors = 
                    "Please correct the errors below:";

                fd._vue.lang.PlumsailForm_Submission_Error = 
                    "An error has occured while saving the form. Please check the console (F12).";

                fd._vue.lang.PlumsailForm_Submission_Success = 
                    "The form has been submitted successfully.";

                fd._vue.lang.RequiredValidator_Error = 
                    "This field is required.";
                    
                fd._vue.lang.SPDataTable_AddNewItem = "Add new item";
                fd._vue.lang.SPDataTable_ListNotFoundError = "List does not exist.";
                fd._vue.lang.SPDataTable_Upload = "Upload";
                fd._vue.lang.SPDataTable_Uploading = "Uploading...";
                fd._vue.lang.SPFormToolbar_Close = "Close";
                fd._vue.lang.SPFormToolbar_Edit = "Edit";
                fd._vue.lang.SPFormToolbar_Save = "Save";
                fd._vue.lang.SPFormToolbar_Saving = "Saving...";

    *   -   **fd.pdfFileName**

        -   Get or set the name of the exported PDF file.

            *This property is only available for* **SharePoint Forms** 
            
            |

            *Example:*
            
            .. code-block:: javascript
                
                //set file name to "My_PDF_File"
                fd.pdfFileName = "My_PDF_File";

                //set file name to current item's Title
                fd.spRendered(function() {
                    fd.pdfFileName = fd.field('Title').value;    
                });

    *   -   **fd.pdfOptions**

        -   Specifies various options for exported PDF file, such as paper size, margin, orientation, etc.

            More info about all the options |PDF options|.

            *This property is only available for* **SharePoint Forms**
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.pdfOptions = {
                    paperSize: 'A4',
                    landscape: true,
                    multiPage: true
                };

.. |PDF options| raw:: html

    <a href="https://docs.telerik.com/kendo-ui/framework/drawing/pdf-output#configuration-PDF" target="_blank">here</a>


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

    *   -   **spBeforeRender()**
        -   Occurs before mounting the vue-component to DOM.

            **сtx** passed as an argument to the function is a SharePoint form context. 

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

            *Note:* This event is exclusive to SharePoint Forms and occurs after **beforeRender()**. 
            
            For Plumsail Forms, use **beforeRender()**.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spBeforeRender(function(ctx) {
                    console.log('spBeforeRender');
                    console.log(ctx);
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

    *   -   **spRendered()**
        -   Occurs after mounting the vue-component to DOM.

            **Best place to run your JavaScript** since all elements are already built and rendered.

            You can also use this event for fields that have custom **ready** event available.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            *Note:* This event is exclusive to SharePoint Forms and occurs after **rendered()**. 
            
            For Plumsail Forms, use **rendered()**.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spRendered(function(vue) {
                    console.log('rendered');
                    console.log(vue);
                });

                fd.spRendered(function() {
                    //simple fields are available
                    fd.field('Title').value = "New Title";

                    //can use ready event for complex fields
                    fd.field('Lookup').ready().then(function(field) {
                        console.log(field.value.LookupValue);
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

            *Note:* This event is exclusive to Plumsail Forms. 
            
            For SharePoint Forms, use **spBeforeSave()**.
            
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

    *   -  **spBeforeSave()**
        -   Occurs before submitting the form.

            **spForm** passed as an argument to the function is a SharePoint client form.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

            *Note:* This event is exclusive to SharePoint Forms and occurs after **beforeSave()**.
            
            For Plumsail Forms, use **beforeSave()**.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spBeforeSave(function(spForm) {
                    console.log('spBeforeSave');
                    console.log(spForm);
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

    *   - **spSaved()**
        -   Occurs after the form is submitted.

            **result** passed as an argument to the function is an object containing additional fields of the SharePoint item: 
            
            *Id*, 
            
            *ItemUrl* (for documents and document sets), 
            
            *RedirectUrl* - URL of a page where a user will be redirected after saving. 
            
            This object can be changed.

            *Note:* This event is exclusive to SharePoint Forms. 
            
            For Plumsail Forms, use **saved()**.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spSaved(function(result) {
                    console.log('spSaved');
                    console.log(result);
                });
    
    
.. |vueConfig| raw:: html

    <a href="https://vuejs.org/v2/guide/instance.html" target="_blank">here</a>