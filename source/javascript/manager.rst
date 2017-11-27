Manager
==================================================

fd global variable
--------------------------------------------------
**fd** is a Forms designer manager variable. Whenever you want to use custom methods on the form, you need to call the manager first. 

 **fd** is not global and only accesible from within the form, e.g. from JavaScript editor. 

 It is accesible globally in Form Preview, so you can run tests from browser's console.

 Otherwise, it will not be accesible globally on the page, so you can include several forms on one page and not worry about their scripts conflicting at all.

Plumsail Forms Events
--------------------------------------------------
These events can be executed from JavaScript editor for Plumsail Forms:

.. list-table::
    :header-rows: 1
    :widths: 6 22 22
        
    *   -   Event
        -   Description
        -   Example
    *   -   **beforeCreate()**
        -   Occurs prior to form creation.
        
            **vueConfig** passed as an argument to the function is a configuration of the main vue-component. You can register your own child components.
            You can read more about it |vueConfig|.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.
        
        - .. code-block:: javascript

            fd.beforeCreate(function(vueConfig) {
                console.log('beforeCreate');
                console.log(vueConfig);
            });

    *   -   **created()**
        -   Occurs as soon as the form is created.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

        - .. code-block:: javascript

            fd.created(function(vue) {
                console.log('created');
                console.log(vue);
            });

    *   -   **beforeRender()**
        -   Occurs before mounting the vue-component to DOM.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

        - .. code-block:: javascript

            fd.beforeRender(function(vue) {
                console.log('beforeRender');
                console.log(vue);
            });

    *   -   **rendered()**
        -   Occurs after mounting the vue-component to DOM.

            **Best place to run your JavaScript** since all elements are already built and rendered.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

        - .. code-block:: javascript

            fd.rendered(function(vue) {
                console.log('rendered');
                console.log(vue);
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

        - .. code-block:: javascript

            fd.beforeSave(function(data) {
                console.log('beforeSave');
                console.log(data);
            });

          *Asynchronous:*

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

        - .. code-block:: javascript

            fd.saved(function() {
                console.log('saved');
            });

    

Modern SharePoint Forms Events
--------------------------------------------------
These events can be executed from JavaScript editor for Modern SharePoint Forms:

.. list-table::
    :header-rows: 1
    :widths: 6 22 22

    *   - Event
        - Description
        - Example
    *   -   **beforeCreate()**
        -   Occurs prior to form creation.
        
            **vueConfig** passed as an argument to the function is a configuration of the main vue-component. You can register your own child components.
            You can read more about it |vueConfig|.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.
        
        - .. code-block:: javascript

            fd.beforeCreate(function(vueConfig) {
                console.log('beforeCreate');
                console.log(vueConfig);
            });

    *   -   **created()**
        -   Occurs as soon as the form is created.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

        - .. code-block:: javascript

            fd.created(function(vue) {
                console.log('created');
                console.log(vue);
            });

    *   -   **spBeforeRender()**
        -   Occurs before mounting the vue-component to DOM.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

        - .. code-block:: javascript

            fd.spBeforeRender(function(vue) {
                console.log('beforeRender');
                console.log(vue);
            });

    *   -   **spRendered()**
        -   Occurs after mounting the vue-component to DOM.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

        - .. code-block:: javascript

            fd.spRendered(function(vue) {
                console.log('rendered');
                console.log(vue);
            });

    *   -  **spBeforeSave()**
        -   Occurs before submitting the form.

            **spForm** passed as an argument to the function is a SharePoint client form.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

        - .. code-block:: javascript

            fd.spBeforeSave(function(spForm) {
                console.log('spBeforeSave');
                console.log(spForm);
            });

    *   - **spSaved()**
        -   Occurs after the form is submitted.

            **result** passed as an argument to the function is an object containing additional fields of the SharePoint item: 
            
            *Id*, 
            
            *ItemUrl* (for documents and document sets), 
            
            *RedirectUrl* - URL of a page where a user will be redirected after saving. 
            
            This object can be changed.

        - .. code-block:: javascript

            fd.spSaved(function(result) {
                console.log('spSaved');
                console.log(result);
            });

.. |vueConfig| raw:: html

    <a href="https://vuejs.org/v2/guide/instance.html" target="_blank">here</a>

Validators
--------------------------------------------------
You can also write and include your own custom Form and Field Validators for Modern Forms.

Use **rendered()** event for Plumsail forms and **spRendered()** event for SharePoint forms to add custom validators.

.. list-table::
    :header-rows: 1
    :widths: 6 22 22
        
    *   -   Validator
        -   Description
        -   Example
    *   -   **Field Validator**
        -   Simple validator for one field, only checks if specific field matches certain criteria or not.

            If the field does not match the criteria, the form will not submit.
        
        - .. code-block:: javascript

            fd.rendered(function(){
                fd.field('Numeric0').validators.push({
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
            });
    
    *   -   **Form Validator**
        -   More complex validator for several fields, checks that different fields have appropriate values.

            For example, you want certain options to be only available if the user's age is above 18 or some other criteria.

            If the fields do not match these criterias, the form will not submit.
        
        - .. code-block:: javascript

            fd.rendered(function(){
                fd.validators.push({
                    name: 'MyCustomValidator',
                    error: "'To' must be greater than 'From'.",
                    validate: function(value) {
                        if (fd.field('From').value >= fd.field('To').value)
                            return false;
                            
                        return true;
                    }
                });
            });

fd methods
--------------------------------------------------
These methods can be applied to **fd**:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Method
        -   Description
        -   Examples
    *   -   **fd.save()**
        -   Saves the form.
        - .. code-block:: javascript

                fd.save();
                
    *   -   **fd.data()**
        -   Gathers data from all fields on the form. Can be used to get or set multiple values at the same time.
        - .. code-block:: javascript

                fd.data();
                fd.data({Field1: value1, Field2: value2});

    *   -   **fd.clear()**
        -   Clears the form.
        - .. code-block:: javascript

                fd.clear();

fd properties
--------------------------------------------------
**fd** has the following properties:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20

    *   -   Property
        -   Description
        -   Examples
    *   -   **fd.culture**
        -   Returns the name of the current culture, e.g. "en-US"
        - .. code-block:: javascript

                fd.culture;

    *   -   **fd.formId**
        -   Returns ID of the form.
        - .. code-block:: javascript

                fd.formId;
    *   -   **fd.isFilesUploadingInProgress**
        -   Returns true if files are currently uploaded as attachments, returns false otherwise.
        - .. code-block:: javascript

                fd.isFilesUploadingInProgress;

    *   -   **fd.isValid**
        -   Checks if form is valid or not. 
            
            Each time the property is called, it runs a method to check if all validators validate succesfully, both Field and Form validators.

            Returns *true* on success. Otherwise, returns *false* and error messages get displayed.
        - .. code-block:: javascript

                fd.isValid;

    *   -   **fd.validators**
        -   Returns an array of form validators, can be used to add new ones.
        - .. code-block:: javascript

                fd.validators;
                fd.validators.push({
                    name: 'MyCustomValidator',
                    error: "Age must be 18 or over.",
                    validate: function(value) {
                        if (fd.field('Age').value < 18)
                            return false;
                            
                        return true;
                    }
                });

    *   -   **fd._vue**
        -   Returns VueJS component of the form, so you can examine or modify it.
        - .. code-block:: javascript

                fd._vue;
    