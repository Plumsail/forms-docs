Controls
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Intro
--------------------------------------------------
Here you can find properties, methods and events of various controls that you can have on your form. 

Insert them into JavaScript editor or inside OnClick setting for buttons and links.

*Internal Name* is the property that is used to identify specific controls and apply methods to them. *Internal Name* is unique for every element on the form.

**Important!** These events, methods and properties shouldn't be used on their own, they must be executed inside events 
like **rendered()** or **beforeSave()** in order to actually access the fields or controls that you target.

If you just add these scripts on their own or inside wrong event in JavaScript editor,
they will not have access to the specified controls, or will execute at the wrong time.
Read more about different events in :doc:`Manager section </javascript/manager>`.

Button
--------------------------------------------------
Properties of the Button control.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **text**
        -   Property that holds text for the button.
        - .. code-block:: javascript

                fd.control('Button0').text;

                fd.control('Button0').text = 
                'New text for button';

    *   -   **onclick**
        -   Property that holds JavaScript that is executed when button is clicked.
        - .. code-block:: javascript

                fd.control('Button0').onclick;

                fd.control('Button0').onclick = 
                'alert("Button is clicked!")';

Submit
--------------------------------------------------
Properties of the Submit control.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **text**
        -   Property that holds text for the submit button.
        - .. code-block:: javascript

                fd.control('Button1').text;
                fd.control('Button1').text = 'New text for button';

    *   -   **onclick**
        -   Property that holds JavaScript that is executed when submit button is clicked.
        - .. code-block:: javascript

                fd.control('Button1').onclick;
                fd.control('Button1').onclick = 'fd.save();';

    *   -   **disabled**
        -   Property that specifies if submit button is clickable or not, can be used to disable submit button.
        - .. code-block:: javascript

                fd.control('Button1').disabled; //returns true or false
                fd.control('Button1').disabled = true;
                fd.control('Button1').disabled = false;
                
    *   -   **isSaving**
        -   Property that checks if form submission is in process.
        - .. code-block:: javascript

                fd.control('Button1').isSaving;

    *   -   **savingText**
        -   Property that holds text that is displayed on form submission.
        - .. code-block:: javascript

                fd.control('Button1').savingText;
                fd.control('Button1').savingText = 
                'Collecting the data...';

Hyperlink
--------------------------------------------------
Properties of the Hyperlink control.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples

    *   -   **text**
        -   Property that holds text for the control.
        - .. code-block:: javascript

                fd.control('Hyperlink0').text;
                fd.control('Hyperlink0').text = 
                'New text for hyperlink';

    *   -   **target**
        -   Property that holds target attribute for the link.

            The target attribute specifies where to open the linked document.

            Most common use is to open linked document in a new tab by setting target to "_blank"
        - .. code-block:: javascript

                fd.control('Hyperlink0').target;
                fd.control('Hyperlink0').target = '_blank';
                
    *   -   **href**
        -   Property that holds href for the link.

            The href attribute specifies the link's destination.

        - .. code-block:: javascript

                fd.control('Hyperlink0').href;
                fd.control('Hyperlink0').href = 'https://plumsail.com/';

    *   -   **onclick**
        -   Property that holds JavaScript that is executed when link is clicked.
        - .. code-block:: javascript

                fd.control('Hyperlink0').onclick;
                fd.control('Hyperlink0').onclick = 
                'alert("Hyperlink is clicked!")';

Image
--------------------------------------------------
Properties of the Image control.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **target**
        -   Property that holds target attribute for the image, used when image works as Hyperlink.

            The target attribute specifies where to open the linked document.

            Most common use is to open linked document in a new tab by setting target to "_blank"
        - .. code-block:: javascript

                fd.control('Image0').target;
                fd.control('Image0').target = '_blank';
                
    *   -   **href**
        -   Property that holds href for the link placed on the image.

            The href attribute specifies the link's destination.

        - .. code-block:: javascript

                fd.control('Image0').href;
                fd.control('Image0').href = 'https://plumsail.com/';

    *   -   **width**
        -   Property that specifies the width of the image.
        - .. code-block:: javascript

                fd.control('Image0').width;
                fd.control('Image0').width = '256';

    *   -   **height**
        -   Property that specifies the height of the image.
        - .. code-block:: javascript

                fd.control('Image0').height;
                fd.control('Image0').height = '512';

    *   -   **source**
        -   Property that specifies the source of the image.

            Source attribute specifies the URL of the image and allows you to link any image to your form.
        - .. code-block:: javascript

                fd.control('Image0').source;
                fd.control('Image0').source = 
                'https://images.com/my-image.png';

    *   -   **alt**
        -   Property that specifies an alternate text for an image, if the image cannot be displayed.
        - .. code-block:: javascript

                fd.control('Image0').alt;
                fd.control('Image0').alt = 
                'This picture is awesome, if only you could see it!';

    *   -   **onclick**
        -   Property that holds JavaScript that is executed when link is clicked.
        - .. code-block:: javascript

                fd.control('Image0').onclick;
                fd.control('Image0').onclick = 
                'alert("Hyperlink is clicked!")';

Plain Text
--------------------------------------------------
Properties of the Plain Text control.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **text**
        -   Property that holds text for the Plain Text control.
        - .. code-block:: javascript

                fd.control('Text0').text;
                fd.control('Text0').text = 'New text for text control';

Ink Sketch
--------------------------------------------------
Properties of the Ink Sketch control.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **value**
        -   Property that holds value of the Ink Sketch control in text.
            Can be copied, stored and set, for example.
        - .. code-block:: javascript

                var signature = fd.control('Signature0').value;
                fd.control('Signature1').value = 'signature';

    *   -   **width**
        -   Property that specifies the width of the ink sketch canvas.
        - .. code-block:: javascript

                fd.control('Signature0').width;
                fd.control('Signature0').width = '128';

    *   -   **height**
        -   Property that specifies the height of the ink sketch canvas.
        - .. code-block:: javascript

                fd.control('Signature0').height;
                fd.control('Signature0').height = '256';
    
    *   -   **readonly**
        -   Property that specifies if user can draw on canvas or not. Takes and returns only *true* and *false* values.
        - .. code-block:: javascript

                fd.control('Signature0').readonly;
                fd.control('Signature0').readonly = true;
                fd.control('Signature0').readonly = false;
    
    *   -   **inkColor**
        -   Property that specifies color of the drawn lines. Can be used to change color dynamically.
        - .. code-block:: javascript

                fd.control('Signature0').inkColor;
                fd.control('Signature0').inkColor = "red"
                fd.control('Signature0').inkColor = "#0F0"
                fd.control('Signature0').inkColor = "#0000FF" 
                fd.control('Signature0').inkColor = "rgb(0,0,0)"

DataTable
--------------------------------------------------
Properties, methods and events of the DataTable control.

Properties
**************************************************

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **columns**
        -   Property that holds all the columns that the DataTable has. 
        
            Returns an array of |Kendo UI Grid columns|.
        - .. code-block:: javascript

                fd.control('DataTable0').columns; // returns an array

                //get the InternalName of the column (can't set!):
                fd.control('DataTable0').columns[0].field; 

                //get the title of the column (can't set!):
                fd.control('DataTable0').columns[0].title; 

                //set column to readonly state:
                fd.control('DataTable0').columns[0].editable = 
                function(){return false}; 

                //set column back to editable state:
                fd.control('DataTable0').columns[0].editable = 
                function(){return true}; 

                //check if column is editable, returns true or false:
                fd.control('DataTable0').columns[0].editable; 
            
    *   -   **value**
        -   Property that holds all the records that the DataTable has. 
            
            Returns an array of objects where each has values matching Internal Column name and their respective value in the DataTable.
            
            Can be used to get information about existing records or create new records.
        - .. code-block:: javascript

                fd.control('DataTable0').value; // returns an array
                
                // add new record to the DataTable using columns' InternalNames:
                var record = {Date: new Date(), Text: "New Text", Cost: 250 };
                fd.control('DataTable0').value.push(record); 
    
    *   -   **widget**
        -   Property that holds |kendoGrid widget| for the DataTable.
            
            Can be used to retrieve it, but not to modify it.
        - .. code-block:: javascript

                fd.control('DataTable0').widget;

Methods
**************************************************

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **addValidator(validator)**
        -   Method that allows you to add DataTable validators for the whole table.

            Accepts validator object as a parameter.

            Inside validator, use **value** to access an array of records inside the DataTable.

            This allows you not only to check individual columns and compare their values,
            but to limit amount of records or set minimum amount, etc.
        - .. code-block:: javascript

                fd.control('DataTable0').addValidator({
                    error: 'Error message',
                    validate: function(value) {
                        if (value.length == 0) {
                            this.error = 
                            "Add at least one record to the table";
                            return false;
                        }
                       
                        if (value.length > 10) {
                            this.error = 
                            "Don't add more than 10 records to the table";
                            return false;
                        }
                       
                        return true;
                    }
                });

    *   -   **addColumnValidator('columnName', validator)**
        -   Method that allows you to add DataTable Column validators for the specific column in a table.

            Users cannot switch focus to other columns until this one is validated.

            Accepts InternalName of the column string and validator object as its parameters.
        - .. code-block:: javascript

                fd.control('DataTable0').addColumnValidator('Column1', {
                    error: 'Error message',
                    validate: function(value) {
                        if (value <= 0) {
                            this.error = 'Value must by greater than 0';
                            return false;
                        }
                       
                        if (value > 100) {
                            this.error = 'Value must be less than 100';
                            return false;
                        }
                       
                        return true;
                    }
                });

Events
**************************************************

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **change**
        -   Fired when the user applies any changes to the table, including adding, deleting or changing records.

            Inside the function, use **value** to access an array of records inside the DataTable.
        - .. code-block:: javascript

                fd.control('DataTable0').$on('change',
                    function(value) {
                        console.log(value); // DataTable's value 
                        alert('DataTable changed');
                    });
    
    *   -   **beforeEdit**
        -   Fired when the user try to edit or create a data item, before the editor is created. 
            Can be used for preventing the editing depending on custom logic.

            Read more here - https://docs.telerik.com/kendo-ui/api/javascript/ui/grid#events-beforeEdit
        - .. code-block:: javascript

                fd.control('DataTable0').$on('beforeEdit',
                    function(e) {
                        console.log(e.model); // log info about record
                        alert('About to edit');
                    });

    *   -   **edit**
        -   Fired when the user edits or creates a data item.

            Read more here - https://docs.telerik.com/kendo-ui/api/javascript/ui/grid#events-edit
        - .. code-block:: javascript

                fd.control('DataTable0').$on('edit',
                    function(e) {
                        console.log(e.model); // log info about record
                        alert('Editing');
                    });

    *   -   **remove**
        -   Fired when the user clicks the "delete" command button and delete operation is confirmed in the confirmation window, 
            if the cancel button in the window is clicked the event will not be fired.

            Read more here - https://docs.telerik.com/kendo-ui/api/javascript/ui/grid#events-remove
        - .. code-block:: javascript

                fd.control('DataTable0').$on('remove',
                    function(e) {
                        console.log(e.model); // log info about record
                        alert('Removed');
                    });
                    

.. |Kendo UI Grid columns| raw:: html

    <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/grid#fields-columns" target="_blank">Kendo UI Grid columns</a>

List or Library
--------------------------------------------------
Properties, methods and events of the List or Library control.

Properties
**************************************************

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **filter**
        -   Property that holds CAML filtering for the control. 
            Empty by default, contains filter value if you choose Lookup Field in Data Source Editor.

            Can also be used to apply filtering. Changes are applied dynamically to the control.
        
        - .. code-block:: javascript

                fd.control('SPDataTable0').filter; // returns CAML string

                //return only items where Title is "Test"
                fd.control('SPDataTable0').filter = 
                    "<Eq><FieldRef Name='Title'/><Value Type='Text'>Test</Value></Eq>";
            
    *   -   **readonly**
        -   Property that specifies if the user can add new items/documents to the control, edit or delete existing items/documents. 
            
            Takes and returns only *true* and *false* values.
        - .. code-block:: javascript

                fd.control('SPDataTable0').readonly;
                fd.control('SPDataTable0').readonly = true;
                fd.control('SPDataTable0').readonly = false;

    *   -   **baseRootFolder**
        -   Property that specifies starting folder for the control. User cannot go higher than this folder. 
            
        - .. code-block:: javascript

                fd.control('SPDataTable0').baseRootFolder;
                //set root as Base Folder:
                fd.control('SPDataTable0').baseRootFolder = '';
                //set folder as Base Folder:
                fd.control('SPDataTable0').baseRootFolder = "Folder1"

    *   -   **rootFolder**
        -   Property that specifies current folder for the control. 
            
        - .. code-block:: javascript

                fd.control('SPDataTable0').rootFolder;
                //set root as Current Folder:
                fd.control('SPDataTable0').rootFolder = '';
                //set Folder1 as Current Folder:
                fd.control('SPDataTable0').rootFolder = "Folder1"

    *   -   **addNewItemText**
        -   Property that holds "Add new item" text, useful for localizations.
            
        - .. code-block:: javascript

                fd.control('SPDataTable0').addNewItemText // "Add new item" by default
                fd.control('SPDataTable0').addNewItemText = "New text"
    
    *   -   **uploadText**
        -   Property that holds "Upload" text, useful for localizations.
            
        - .. code-block:: javascript

                fd.control('SPDataTable0').uploadText // "Upload" by default
                fd.control('SPDataTable0').uploadText = "New text"
    
    *   -   **uploadingText**
        -   Property that holds "Uploading..." text, useful for localizations.
            
        - .. code-block:: javascript

                fd.control('SPDataTable0').uploadingText // "Uploading..." by default
                fd.control('SPDataTable0').uploadingText = "New text"
    
    *   -   **dialogOptions**
        -   Property that holds dialog options object which specifies width and height of the dialog window.
            
        - .. code-block:: javascript

                fd.control('SPDataTable0').dialogOptions.height; //returns height
                fd.control('SPDataTable0').dialogOptions.width //returns width

                //set width and height:
                fd.control('SPDataTable0').dialogOptions = {
                        width: 1280,
                        height: 720
                    }
    
    *   -   **widget**
        -   Property that holds |kendoGrid widget| for the control.
            
            Can be used to retrieve it, but not to modify.
        - .. code-block:: javascript

                fd.control('SPDataTable0').widget;

Events
**************************************************

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **filesUploaded**
        -   Fired when the user uploads files to Document Library via List or Library control.

            **itemIds** is an array of IDs of uploaded files.
        - .. code-block:: javascript

                //log all uploaded files to console
                fd.control('SPDataTable0').$on('filesUploaded',
                    function(itemIds) {
                        itemIds.forEach(function(item) {
                            console.log(item);
                        });
                    });
    
    *   -   **ready**
        -   Triggers when the control is initialized and is ready to be used in scripts. 
        - .. code-block:: javascript

                fd.spRendered(function() {
                    fd.control('SPDataTable0').$on('ready', function(dt) { 
                        //dt parameter is the same as fd.control('SPDataTable0')
                        console.log('SPDataTable0 is initialized');
                    });
                });

    *   -   **beforeItemsAttach**
        -   Fired when saving New Form that has items in Library or List control, that will be tied to the parent via lookup field.

            Function contains parameter object with the following properties:

            **itemIds** is an array of IDs of uploaded files.

            **lookupField** is a Lookup field on children items, that binds them to parent.

            **parentItemId** is an ID of the newly saved Parent item
        - .. code-block:: javascript

                //give an alert message when saving New Form
                fd.control('SPDataTable0').beforeItemsAttach(function(e) {
                    return new Promise(function(resolve) {
                        var ids = '';
                        var message = 'Item(s): ' + e.itemIds.join();
                        message += ' attached to Parent with ID: ' + e.parentItemId;
                        message += ' via Lookup: ' + e.lookupField;

                        alert(message);

                        //once resolved, the form will save:
                        resolve();
                    })
                });
    

.. |kendoGrid widget| raw:: html

    <a href="https://docs.telerik.com/kendo-ui/api/javascript/ui/grid" target="_blank">kendoGrid widget</a>