Managing containers with JavaScript in Plumsail Forms for SharePoint
============================================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Intro
--------------------------------------------------
Here you can find properties of the containers that you can have on your form and methods that can be used on them. 

Insert them into JavaScript editor or inside OnClick setting for buttons and links.

*Internal Name* is the property that is used to identify specific containers(Tab Control, Accordion or Wizard) and apply methods to them. 
*Internal Name* is unique for every element on the form.

.. important::  These events, methods and properties shouldn't be used on their own, they must be executed inside events 
                like **spRendered()** or **spBeforeSave()** in order to actually access the fields or controls that you target.

                If you just add these scripts on their own or inside wrong event in JavaScript editor,
                they will not have access to the specified containers, or will execute at the wrong time.
                Read more about different events in :doc:`Manager section </javascript/manager>`.

For more use cases, check out :doc:`our manual </how-to/conditional-containers>` on how-to adjust containers dynamically on your form.

Accordion
--------------------------------------------------
Properties of the Accordion container.

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Name
        -   Description/Examples

    *   -   **mode**
        -   Property that holds value for the current mode of Accordion.

            Returns values "One", "ZeroOrOne" and "ZeroOrMultiple".

            Can also be used to set mode, but is not applied dynamically, so best used with Accordion Panel's toggle() method.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Accordion0').mode;
                
                // set mode to Single:
                fd.container('Accordion0').mode = "One";
                // open first panel:
                fd.container('Accordion0').$children[0].toggle(); 

    *   -   **$children**
        -   Property that holds an array of all the panels inside the Accordion.
            Most commonly used to get panels and their methods, but can also be used to add new panels.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.container('Accordion0').$children;

Accordion Panels
--------------------------------------------------
Properties and methods of Accordion panels which can be accessed through **$children** property of the Accordion.

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Name
        -   Description/Examples

    *   -   **header**
        -   Property that holds the header for the panel.

            Can be used to get and set its value.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Accordion0').$children[0].header;
                fd.container('Accordion0').$children[1].header = 'New Header';
    
    *   -   **open**
        -   Property that checks if the panel is open or not.

            Can also be used to open or close a panel ignoring the current mode of the Accordion.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Accordion0').$children[0].open;
                fd.container('Accordion0').$children[1].open = true;
                fd.container('Accordion0').$children[2].open = false;

    *   -   **toggle()**
        -   Method that toggles the state of the panel between open and closed.

            This method does not ignore the current mode of Accordion and acts more like a click from the user.

            Works well with changing Mode of the Accordion, as it updates the state of Accordion to the new Mode.
            Usually doesn't need extra conditions in this case.
            
            |

            *Examples:*
            
            .. code-block:: javascript
                
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
    :widths: 10 30
        
    *   -   Name
        -   Description/Examples
    
    *   -   **tabs**
        -   Property that holds an array with all the tabs.
            Can be used to get existing tabs or add new ones.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.container('Tab0').tabs;
                
    *   -   **currentTab**
        -   Property that holds the position of currently opened tab in the array of tabs. 

            **Important!** Do not use for changing the current tab, only for getting it.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.container('Tab0').currentTab;

    *   -   **orientation**
        -   Property that holds the orientation of the tabs, their position relative to the content inside.

            Returns current value and also can be used to change orientation dynamically.
            Accepts values 'top', 'left', 'bottom' and even 'right'.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Tab0').orientation;
                fd.container('Tab0').orientation = 'left';
    
    *   -   **nextTab()**
        -   Method that selects next tab as active.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.container('Tab0').nextTab();

    *   -   **previousTab()**
        -   Method that selects previous tab as active.
            
            |

            *Example:*
            
            .. code-block:: javascript

                fd.container('Tab0').previousTab();

    *   -   **setTab(int tabIndex)**
        -   Method that selects tab as active.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                //set first tab as active
                fd.container('Tab0').setTab(0);
                //set last tab as active 
                fd.container('Tab0').setTab(
                    fd.container('Tab0').tabs.length -1
                );

Wizard
--------------------------------------------------

Properties 
""""""""""""""""""""""""""""""""""""

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Name
        -   Description/Examples

    *   -   **widget.tabs**
        -   Gets or sets the array of steps.

            Can be used to hide/show tabs or change its order. 

            |

            *Examples:*

            .. code-block:: javascript  

                //get an array of steps 
                fd.container('Wizard0').widget.tabs;

                // Swap the first two steps  
                var tab1 = fd.container('Wizard0').widget.tabs[0]; 
                fd.container('Wizard0').widget.tabs.splice(1, 0, tab1);

                // Hide or show the second step on toggle change  
                function toggleTab2(tab2) {  

                    var isToggle = fd.field('Toggle0').value;  

                    if (isToggle) {
                        // Hide the second tab
                        fd.container('Wizard0').widget.tabs.splice(1, 1);
                    }  

                    if (!isToggle && tab2 !== null) {
                        // Show the second tab 
                        fd.container('Wizard0').widget.tabs.splice(1, 0, tab2)
                    }  
                }  
                
                fd.spRendered(function() {
                    var tab2 = fd.container('Wizard0').widget.tabs[1];
                    
                    // Calling function when the user switchs the toggle
                    fd.field('Toggle0').$on('change', function() { 
                        toggleTab2(tab2); 
                        }); 
                        
                    // Calling function on form loading
                    toggleTab2(tab2);
                });             

    *   -   **widget.activeTabIndex**
        -   Gets the index of the currently selected step.
            
            |

            *Example:*

            .. code-block:: javascript

                fd.container('Wizard0').widget.activeTabIndex; 

    *   -   **backText**
        -   Property that holds text of the Back button, can be used to get it or set it.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Wizard0').backText;
                fd.container('Wizard0').backText = 'Return';

    *   -   **finishText**
        -   Property that holds text of the Finish button, can be used to get it or set it.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Wizard0').finishText;
                fd.container('Wizard0').finishText = 'Submit';

    *   -   **nextText**
        -   Property that holds text of the Next button, can be used to get it or set it.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Wizard0').nextText;
                fd.container('Wizard0').nextText = 'Forward';
    *   -   **shape**
        -   Property that holds the Shape of the UI icons, can be used to get it or set it.

            If the value set is incorrect, shape reverts to Circle.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Wizard0').shape;
                fd.container('Wizard0').shape = 'circle';
                fd.container('Wizard0').shape = 'square';
                fd.container('Wizard0').shape = 'tab';

    *   -   **steps**
        -   Property that holds an array of the titles for each step, can be used to get it or set them.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Wizard0').steps;
                fd.container('Wizard0').steps = ['Step 1', 'Step 2', 'Step 3'];

    *   -   **icons**
        -   Property that holds an array of |Microsoft Fabric Icons| for each step, can be used to get it or set them.

            By default each step is represented by a number, but this can be changed.
            
            |

            *Examples:*
            
            .. code-block:: javascript

                fd.container('Wizard0').icons;
                fd.container('Wizard0').icons = ['BoxCheckmarkSolid', 'BoxAdditionSolid', 'BranchSearch'];

Methods
""""""""""""""""""""""""""""""""""""

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Name
        -   Description/Examples

    *   -   **widget.activateAll()**
        -   Activates all steps as if the user went through all steps.
            Doesn't trigger validation 

            |

            *Example:*

            .. code-block:: javascript

                fd.container('Wizard0').widget.activateAll(); 

    *   -   **widget.navigateToTab(tabIndex)**
        -   Opens a specific step. The step must be activated. 
            Triggers validation. 

            |

            *Example:*

            .. code-block:: javascript

                //opens the second step 
                fd.container('Wizard0').widget.navigateToTab(1);  

    *   -   **widget.changeTab(oldIndex, newIndex)**
        -   Navigates from one step to another.
            Doesn't trigger validation 

            |

            *Example:*

            .. code-block:: javascript

                //opens  the third step 
                fd.container('Wizard0').widget.changeTab(0,2);  

Events
""""""""""""""""""""""""""""""""""""

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Name
        -   Description/Examples

    *   -   **update:startIndex**
        -   An event that is raised when a user switches between steps.
            
            |

            *Example:*

            .. code-block:: javascript

                //if on step 0, go directly to 2, skipping step 1
                fd.container("Wizard0").widget.$on("update:startIndex", function() {
                    if (fd.container("Wizard0").widget.activeTabIndex == 0){
                        window.setTimeout(function() {
                            fd.container("Wizard0").widget.navigateToTab(2)}, 100)
                    }
                })

    *   -   **on-complete**
        -   An event that is raised when a user finishes the wizard steps.
            
            |

            *Example:*

            .. code-block:: javascript

                fd.container("Wizard0").widget.$on("on-complete", function() {  
                    alert('Wizard steps are completed!'); 
                }); 
 

.. |Microsoft Fabric Icons| raw:: html

    <a href="https://developer.microsoft.com/en-us/fabric#/styles/icons" target="_blank">Microsoft Fabric Icons</a>