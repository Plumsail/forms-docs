Containers
==================================================

Intro
--------------------------------------------------
Here you can find properties of the containers that you can have on your form and methods that can be used on them. 

Insert them into JavaScript editor or inside OnClick setting for buttons and links.

*Internal Name* is the property that is used to identify specific containers(Tab Control and Accordion) and apply methods to them. 
*Internal Name* is unique for every element on the form.

**Important!** These events, methods and properties shouldn't be used on their own, they must be executed inside events 
like **rendered()** or **beforeSave()** in order to actually access the fields or controls that you target.

If you just add these scripts on their own or inside wrong event in JavaScript editor,
they will not have access to the specified containers, or will execute at the wrong time.
Read more about different events in :doc:`Manager section </javascript/manager>`.

For more use cases, check out :doc:`our manual </how-to/conditional-containers>` on how-to adjust containers dynamically on your form.

Accordion
--------------------------------------------------
Properties of the Accordion container.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples

    *   -   **mode**
        -   Property that holds value for the current mode of Accordion.

            Returns values "One", "ZeroOrOne" and "ZeroOrMultiple".

            Can also be used to set mode, but is not applied dynamically, so best used with Accordion Panel's toggle() method.
        - .. code-block:: javascript

                fd.container('Accordion0').mode;
                
                // set mode to Single:
                fd.container('Accordion0').mode = "One";
                // open first panel:
                fd.container('Accordion0').$children[0].toggle(); 

    *   -   **$children**
        -   Property that holds an array of all the panels inside the Accordion.
            Most commonly used to get panels and their methods, but can also be used to add new panels.
        
        - .. code-block:: javascript

                fd.container('Accordion0').$children;

Accordion Panels
--------------------------------------------------
Properties and methods of Accordion panels which can be accessed through **$children** property of the Accordion.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples

    *   -   **header**
        -   Property that holds the header for the panel.

            Can be used to get and set its value.

        - .. code-block:: javascript

                fd.container('Accordion0').$children[0].header;
                fd.container('Accordion0').$children[1].header = 'New Header';
    
    *   -   **open**
        -   Property that checks if the panel is open or not.

            Can also be used to open or close a panel ignoring the current mode of the Accordion.

        - .. code-block:: javascript

                fd.container('Accordion0').$children[0].open;
                fd.container('Accordion0').$children[1].open = true;
                fd.container('Accordion0').$children[2].open = false;

    *   -   **toggle()**
        -   Method that toggles the state of the panel between open and closed.

            This method does not ignore the current mode of Accordion and acts more like a click from the user.

            Works well with changing Mode of the Accordion, as it updates the state of Accordion to the new Mode.
            Usually doesn't need extra conditions in this case.
        
        - .. code-block:: javascript
                
                var accordion = fd.container('Accordion0');

                //opens panel if it is closed
                if (accordion.$children[0].open == false){
                    accordion.$children[0].toggle();
                }

                //closes panel if it is open
                 if (.$children[1].open == true){
                    accordion.$children[1].toggle();
                }
                
                //toggles the panel from one state to another
                accordion.$children[2].toggle();

Tab Control
--------------------------------------------------
Properties and methods of the Tab Control container.

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   -   Name
        -   Description
        -   Examples
    
    *   -   **tabs**
        -   Property that holds an array with all the tabs.
            Can be used to get existing tabs or add new ones.

        - .. code-block:: javascript

                fd.container('Tab0').tabs;
                
    *   -   **currentTab**
        -   Property that holds the position of currently opened tab in the array of tabs. 

            **Important!** Do not use for changing the current tab, only for getting it.

        - .. code-block:: javascript

                fd.container('Tab0').currentTab;

    *   -   **orientation**
        -   Property that holds the orientation of the tabs, their position relative to the content inside.

            Returns current value and also can be used to change orientation dynamically.
            Accepts values 'top', 'left', 'bottom' and even 'right'.
        - .. code-block:: javascript

                fd.container('Tab0').orientation;
                fd.container('Tab0').orientation = 'left';
    
    *   -   **nextTab()**
        -   Method that selects next tab as active.
        - .. code-block:: javascript

                fd.container('Tab0').nextTab();

    *   -   **previousTab()**
        -   Method that selects previous tab as active.
        - .. code-block:: javascript

                fd.container('Tab0').previousTab();

    *   -   **setTab(int tabIndex)**
        -   Method that selects tab as active.
        - .. code-block:: javascript

                //set first tab as active
                fd.container('Tab0').setTab(0);
                //set last tab as active 
                fd.container('Tab0').setTab(
                    fd.container('Tab0').tabs.length -1
                );