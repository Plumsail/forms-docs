.. title:: Managing dialog with JS

.. meta::
   :description: Dialog's JavaScript API with properties and methods in Plumsail Forms for SharePoint

Managing dialogs in SharePoint form with JavaScript in Plumsail Forms for SharePoint
================================================================================================

**Dialog** can be used to open other forms in dialog from a parent form. Can open multiple dialogs at the same time, but only the last one will be active.
Can also open forms in dialog from other forms opened in dialog.

.. contents:: Contents:
 :local:
 :depth: 1
 
Methods
--------------------------------------------------
These methods are applicable to most fields:

.. list-table::
    :header-rows: 1
    :widths: 10 30
        
    *   -   Method
        -   Description/Examples
    
    *   -   **open(url, arguments, callback(bool, args), options)**
        -   Opens form in dialog.

            **url** - url to open in dialog (only works for URLs on the same domain).

            **arguments** - JS object to pass arguments to the form opened in dialog.

            **callback(bool, args)** - function called when dialog is closed. Takes two parameters: 
            
            * *bool* - returns true if the form in dialog was saved, 
            
            * *args* - JS object which can be used to pass arguments from the closing form (need to use **Dialog.close(bool, args)**).

            **options** - JS object which specifies dialog window options.
            
            |

            *Example:*
            
            .. code-block:: javascript

                Dialog.open("https://mycompany.sharepoint.com/sites/mysite/_layouts/15/listform.aspx?PageType=8&ListId=" + listId, 
                    { args: 'something' }, function(hasSaved) {
                    if(hasSaved){
                        alert('Form in dialog has saved and closed.');
                    }
                    else{
                        alert('Dialog form was closed without saving!');
                    }          
                }, { width: 600, height: 600  });

            Read more about generation of form URLs :doc:`here</how-to/link-to-form>`.
        
    *   -   **getArgs()**
        -   Get arguments passed to a dialog.

            Can be called from both parent and child form, but generally more useful on child form.

            On parent form, returns arguments passed to the last opened dialog form.

            On child form, returns arguments passed to the this dialog form.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //code for Parent Form to pass New Title
                Dialog.open("https://mycompany.sharepoint.com/sites/mysite/_layouts/15/listform.aspx?PageType=8&ListId=" + listId, 
                    { passedTitle: 'New Title' });

                //code for Child Form to retrieve New Title
                fd.spRendered(function() {
                    //if opened in dialog
                    if (window.frameElement && Dialog.getArgs()){
                        //set Title to passedTitle property
                        fd.field("Title").value = Dialog.getArgs().passedTitle;
                    }
                });

            Read more about generation of form URLs :doc:`here</how-to/link-to-form>`.

    *   -   **close(bool, args)**
        -   Close dialog form.

            Can be called from both parent and child form.

            On parent form, closes the last active dialog form.

            On child form, closes this specific dialog form.
            
            |

            *Example:*
            
            .. code-block:: javascript

                //code for Parent Form to show created Item ID in alert
                Dialog.open("https://mycompany.sharepoint.com/sites/mysite/_layouts/15/listform.aspx?PageType=8&ListId=" + listId, 
                    { args: 'something' }, function(hasSaved, returnedArgs) {
                    if(hasSaved){
                        alert('Form in dialog has been saved. New Item ID: ' + returnedArgs.ID);
                    }
                    else{
                        alert('Dialog form was closed without saving!');
                    }          
                });

                //code for Child Form to pass ID after save
                fd.spSaved(function(result) {
                    //if opened in dialog
                    if (window.frameElement && Dialog.getArgs()){
                        Dialog.close(true, {ID: result.Id });
                    }
                });

            Read more about generation of form URLs :doc:`here</how-to/link-to-form>`.