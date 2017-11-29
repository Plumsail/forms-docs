Controls
==================================================

Intro
--------------------------------------------------
Here you can find properties of various controls that you can have on your form. 

Insert them into JavaScript editor or inside OnClick setting for buttons and links.

*Internal Name* is the property that is used to identify specific controls and apply methods to them. *Internal Name* is unique for every control.

**Important!** These events, methods and properties shouldn't be used on their own, they must be executed inside events 
like **rendered()** or **beforeSave()** in order to actually access the fields or controls that you target.

If you just add these scripts on their own or inside wrong event in JavaScript editor,
they will not have access to the specified fields or controls, or will execute at the wrong time.
Read more about different events in :doc:`Manager section </javascript/manager>`.

Button
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **control(internalName).text**
        -   Property that holds text for the button.
        - .. code-block:: javascript

                fd.control('Button0').text;

                fd.control('Button0').text = 
                'New text for button';
    *   -   **control(internalName).onclick**
        -   Property that holds JavaScript that is executed when button is clicked.
        - .. code-block:: javascript

                fd.control('Button0').onclick;

                fd.control('Button0').onclick = 
                'alert("Button is clicked!")';

Button
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **control(internalName).text**
        -   Property that holds text for the submit button.
        - .. code-block:: javascript

                fd.control('Button1').text;
                fd.control('Button1').text = 'New text for button';
    *   -   **control(internalName).onclick**
        -   Property that holds JavaScript that is executed when submit button is clicked.
        - .. code-block:: javascript

                fd.control('Button1').onclick;
                fd.control('Button1').onclick = 'fd.save();';

    *   -   **control(internalName).disabled**
        -   Property that specifies if submit button is clickable or not, can be used to disable submit button on some conditions.
        - .. code-block:: javascript

                fd.control('Button1').disabled;
                fd.control('Button1').disabled = true;
                fd.control('Button1').disabled = false;
    *   -   **control(internalName).isSaving**
        -   Property that checks if form submission is in process.
        - .. code-block:: javascript

                fd.control('Button1').isSaving;

    *   -   **control(internalName).savingText**
        -   Property that holds text that is displayed on form submission.
        - .. code-block:: javascript

                fd.control('Button1').savingText;
                fd.control('Button1').savingText = 
                'Collecting the data...';

Hyperlink
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples

    *   -   **control(internalName).text**
        -   Property that holds text for the control.
        - .. code-block:: javascript

                fd.control('Hyperlink0').text;
                fd.control('Hyperlink0').text = 
                'New text for hyperlink';

    *   -   **control(internalName).target**
        -   Property that holds target attribute for the link.

            The target attribute specifies where to open the linked document.

            Most common use is to open linked document in a new tab by setting target to "_blank"
        - .. code-block:: javascript

                fd.control('Hyperlink0').target;
                fd.control('Hyperlink0').target = '_blank';
                
    *   -   **control(internalName).href**
        -   Property that holds href for the link.

            The href attribute specifies the link's destination.

        - .. code-block:: javascript

                fd.control('Hyperlink0').href;
                fd.control('Hyperlink0').href = 'https://plumsail.com/';

    *   -   **control(internalName).onclick**
        -   Property that holds JavaScript that is executed when link is clicked.
        - .. code-block:: javascript

                fd.control('Hyperlink0').onclick;
                fd.control('Hyperlink0').onclick = 
                'alert("Hyperlink is clicked!")';

Image
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **control(internalName).target**
        -   Property that holds target attribute for the image, used when image works as Hyperlink.

            The target attribute specifies where to open the linked document.

            Most common use is to open linked document in a new tab by setting target to "_blank"
        - .. code-block:: javascript

                fd.control('Image0').target;
                fd.control('Image0').target = '_blank';
                
    *   -   **control(internalName).href**
        -   Property that holds href for the link placed on the image.

            The href attribute specifies the link's destination.

        - .. code-block:: javascript

                fd.control('Image0').href;
                fd.control('Image0').href = 'https://plumsail.com/';

    *   -   **control(internalName).width**
        -   Property that specifies the width of the image.
        - .. code-block:: javascript

                fd.control('Image0').width;
                fd.control('Image0').width = '256';

    *   -   **control(internalName).height**
        -   Property that specifies the height of the image.
        - .. code-block:: javascript

                fd.control('Image0').height;
                fd.control('Image0').height = '512';

    *   -   **control(internalName).source**
        -   Property that specifies the source of the image.

            Source attribute specifies the URL of the image and allows you to link any image to your form.
        - .. code-block:: javascript

                fd.control('Image0').source;
                fd.control('Image0').source = 
                'https://images.com/my-image.png';

    *   -   **control(internalName).alt**
        -   Property that specifies an alternate text for an image, if the image cannot be displayed.
        - .. code-block:: javascript

                fd.control('Image0').alt;
                fd.control('Image0').alt = 
                'This picture is awesome, if only you could see it!';

    *   -   **control(internalName).onclick**
        -   Property that holds JavaScript that is executed when link is clicked.
        - .. code-block:: javascript

                fd.control('Image0').onclick;
                fd.control('Image0').onclick = 
                'alert("Hyperlink is clicked!")';

Plain Text
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **control(internalName).text**
        -   Property that holds text for the Plain Text control.
        - .. code-block:: javascript

                fd.control('Text0').text;
                fd.control('Text0').text = 'New text for text control';

Ink Sketch
--------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **control(internalName).value**
        -   Property that holds value of the Ink Sketch control in text.
            Can be copied, stored and set, for example.
        - .. code-block:: javascript

                var signature = fd.control('Signature0').value;
                fd.control('Signature1').value = 'signature';

    *   -   **control(internalName).width**
        -   Property that specifies the width of the ink sketch canvas.
        - .. code-block:: javascript

                fd.control('Signature0').width;
                fd.control('Signature0').width = '128';

    *   -   **control(internalName).height**
        -   Property that specifies the height of the ink sketch canvas.
        - .. code-block:: javascript

                fd.control('Signature0').height;
                fd.control('Signature0').height = '256';
    
    *   -   **control(internalName).readonly**
        -   Property that specifies if user can draw on canvas or not. Takes and returns only *true* and *false* values.
        - .. code-block:: javascript

                fd.control('Signature0').readonly;
                fd.control('Signature0').readonly = true;
                fd.control('Signature0').readonly = false;
    
    *   -   **control(internalName).inkColor**
        -   Property that specifies color of the drawn lines. Can be used to change color dynamically.
        - .. code-block:: javascript

                fd.control('Signature0').inkColor;
                fd.control('Signature0').inkColor = "red"
                fd.control('Signature0').inkColor = "#0F0"
                fd.control('Signature0').inkColor = "#0000FF" 
                fd.control('Signature0').inkColor = "rgb(128,128,128)"

