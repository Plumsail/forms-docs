Manager
==================================================

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
    :widths: 10 20 20

    *   -   Property
        -   Description
        -   Examples
    *   -   **fd.culture**

        -   Returns the name of the current culture.

        - .. code-block:: javascript

                fd.culture; //"en-US"

    *   -   **fd.formId**
        -   Returns ID of the form.
        - .. code-block:: javascript

                fd.formId; //"b5257750-2483-4bea-ac1a-79ad7c670756"

    *   -   **fd.isFilesUploadingInProgress**

        -   Returns *true* if files are currently uploaded as attachments, returns *false* otherwise.

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
            These are more complex validators than Field Validators and are used for several fields, to check that different fields have appropriate values.

            For example, you want certain options to be only available if the user's age is above 18 or some other criteria.

            If the fields do not match these criterias, the form will not submit.

            Use **rendered()** event for Plumsail forms and **spRendered()** event for SharePoint forms to add custom validators.

        - .. code-block:: javascript

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

        -   Returns **VueJS** component of the form, so you can examine or modify it.

        - .. code-block:: javascript

                fd._vue;

Methods
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

Events
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

            *Note:* This event is exclusive to Plumsail Forms. 
            
            For SharePoint Forms, use **spBeforeRender()**.

        - .. code-block:: javascript

            fd.beforeRender(function(vue) {
                console.log('beforeRender');
                console.log(vue);
            });

    *   -   **spBeforeRender()**
        -   Occurs before mounting the vue-component to DOM.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

            *Note:* This event is exclusive to SharePoint Forms. 
            
            For Plumsail Forms, use **beforeRender()**.

        - .. code-block:: javascript

            fd.spBeforeRender(function(vue) {
                console.log('beforeRender');
                console.log(vue);
            });
    
    *   -   **rendered()**
        -   Occurs after mounting the vue-component to DOM.

            **Best place to run your JavaScript** since all elements are already built and rendered.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            *Note:* This event is exclusive to Plumsail Forms. 
            
            For SharePoint Forms, use **spRendered()**.

        - .. code-block:: javascript

            fd.rendered(function(vue) {
                console.log('rendered');
                console.log(vue);
            });

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

    *   -   **spRendered()**
        -   Occurs after mounting the vue-component to DOM.

            **Best place to run your JavaScript** since all elements are already built and rendered.

            **vue** passed as an argument to the function is a Vue instance of the form. 
            
            It is also available from fd variable this way: *fd._vue*

            *Note:* This event is exclusive to SharePoint Forms. 
            
            For Plumsail Forms, use **rendered()**.

        - .. code-block:: javascript

            fd.spRendered(function(vue) {
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

            *Note:* This event is exclusive to Plumsail Forms. 
            
            For SharePoint Forms, use **spBeforeSave()**.

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

    *   -  **spBeforeSave()**
        -   Occurs before submitting the form.

            **spForm** passed as an argument to the function is a SharePoint client form.

            **Asynchronous event!**  Can return a Promise and the corresponding operation will not continue until the promise is resolved.

            *Note:* This event is exclusive to SharePoint Forms. 
            
            For Plumsail Forms, use **beforeSave()**.

        - .. code-block:: javascript

            fd.spBeforeSave(function(spForm) {
                console.log('spBeforeSave');
                console.log(spForm);
            });


    *   -   **saved()**
        -   Occurs after the data is sent to the Flow.

            Can be used to display confirmation message after the form is saved or perform some other actions.

            *Note:* This event is exclusive to Plumsail Forms. 
            
            For SharePoint Forms, use **spSaved()**.

        - .. code-block:: javascript

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

        - .. code-block:: javascript

            fd.spSaved(function(result) {
                console.log('spSaved');
                console.log(result);
            });
    
.. |vueConfig| raw:: html

    <a href="https://vuejs.org/v2/guide/instance.html" target="_blank">here</a>