.. title:: Managing form with JavaScript

.. meta::
   :description: JavaScript API for managing the form in Plumsail Forms for SharePoint

Managing form with JavaScript in Plumsail Forms for SharePoint
========================================================================

**fd** is a Forms designer manager variable. Whenever you want to use custom methods on the form, you need to call the manager first. 

**fd** is not global and only accesible from within the form, e.g. from JavaScript editor, so you can include several forms on one page and not worry about their scripts conflicting at all.

.. contents::
 :local:
 :depth: 1
 
Properties
--------------------------------------------------
**fd** has the following properties:

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Property
        -   Description/Examples

    *   -   **fd.itemId**
        -   Returns ID of the current SharePoint item as string, on Edit or Display form. 

            *Only works with* **SharePoint Forms**.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.itemId; //"1"

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
                    
                fd.messages.SPDataTable_AddNewItem = "Add new item";
                fd.messages.SPDataTable_ListNotFoundError = "List does not exist.";
                fd.messages.SPDataTable_Upload = "Upload";
                fd.messages.SPDataTable_Uploading = "Uploading...";
                fd.messages.SPFormToolbar_Close = "Close";
                fd.messages.SPFormToolbar_Edit = "Edit";
                fd.messages.SPFormToolbar_Save = "Save";
                fd.messages.SPFormToolbar_Saving = "Saving...";

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

    *   -   **fd.exportToPDF(fileName, options)**
        -   Exports current form to PDF file, and starts file download.

            **fileName** passed as an argument to the function is a string with the name of the created file.

            **options** passed as an argument to the function is a JavaScript object that specifies various options for created PDF file, such as paper size, margin, orientation, etc.

            More info about all the options |PDF options|.
            
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

    *   -   **spBeforeRender()**
        -   Occurs before mounting the vue-component to DOM.

            **ctx** passed as an argument to the function is a SharePoint form context. 

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
    
    *   -   **spRendered()**
        -   Occurs after mounting the vue-component to DOM.

            **Best place to run your JavaScript** since all elements are already built and rendered. 
            
            It's also here that fields with *ready* event should be executed inside.

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

                //return next tick if you plan to change any values
                fd.spBeforeSave(function(spForm) {
                    fd.field('FieldName').value = 'New value';
                    return fd._vue.$nextTick();
                });


    *   - **spSaved()**
        -   Occurs after the form is submitted.
            
            **Note:** This event is exclusive to SharePoint Forms. For Plumsail Forms, use **saved()**.

            **result** passed as an argument to the function. It is an object that contains additional fields of the SharePoint item: 
            
            - *Id* - returns the ID of the item.
            
            - *FileLeafRef* - returns the name of the document and document set.
            
            - *RedirectUrl* - holds the URL of a page where a user will be redirected after saving. This object can be changed.
            **Note**: RedirectUrl is ignored inside a panel.
           
            |

            *Example:*
            
            .. code-block:: javascript

                fd.spSaved(function(result) {
                    console.log('spSaved');
                    console.log(result);
                });
    
    
.. |vueConfig| raw:: html

    <a href="https://vuejs.org/v2/guide/instance.html" target="_blank">here</a>