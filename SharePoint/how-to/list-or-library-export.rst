.. title:: Add start flow button to the toolbar of List or Library

.. meta::
   :description: Example of how to add a button that will start flow on press and send selected items to MS Power Automate

How to start flow from List or Library control and pass selected items
===========================================================================

List or Library control allows selection of multiple items, which can then be manipulated in a variety of ways.

|multiple|

.. |multiple| image:: ../images/designer/controls/ListOrLibraryMultiple.png
   :alt: Multiple items can be selected

In this article we'll show you how you can add a new button to List or Library control which will start a new Flow, and use selected items to create a PDF invoice.

.. contents:: Contents:
 :local:
 :depth: 1
 
Form configuration
--------------------------------------------------
First, create form a with List or Library control. We'll use Order form with Order items in List or Library:

|pic1|

.. |pic1| image:: ../images/how-to/list-or-library-export/OrderItems.png
   :alt: List or Library export

We'll use JavaScript to add a new button:

.. code-block:: javascript

    //this URL needs to be updated
    var url = 'FLOW_URL';

    fd.spRendered(function() {
        //new button
        var pdfButton = {
            text: 'Email PDF invoice',
            class: 'btn-secondary',
            visible: false,
            icon: 'PDF',
            iconType: 0,
            click: function() {
                //get item IDs of selected items
                var itemIds = fd.control('SPDataTable0').selectedItems.map(function(item){ return item.ID} );

                //send a request to start flow
                fetch(url, {
                    method: 'POST',
                    body: JSON.stringify({ids: itemIds}), 
                    headers:{
                    'Content-Type': 'application/json'
                    }
                })
                .then(function(response) {
                    if (response.status !== 202) {
                    alert('Looks like there was a problem. Status Code: ' + response.status);
                    } else {
                    alert('Please, check your e-mail.');
                    }
                })
            }
        }

        fd.control('SPDataTable0').ready().then(function(dt) {
            //dt parameter is the same as fd.control('SPDataTable0')
            dt.buttons.push(pdfButton);

            dt.$watch('selectedItems', function(items) {
                pdfButton.visible = items && items.length > 0 ;
            });
        });

    });
        

This JavaScript code will allow button to show up only when some items are selected. This button would send a POST request to MS Flow with the IDs of currently selected items.

Flow
--------------------------------------------------
Create a new Flow from blank, and search for Request connector - **When a HTTP request is received**:

|pic2|

.. |pic2| image:: ../images/how-to/list-or-library-export/FlowSearch.png
   :alt: Search for Request connector

Give it the following Request Body JSON schema:

.. code-block:: javascript

    {
        "type": "object",
        "properties": {
            "ids": {
                "type": "array",
                "items": {
                    "type": "integer"
                }
            }
        }
    }

Next search for Variables connector - **Initialize variable**:

|pic3|

.. |pic3| image:: ../images/how-to/list-or-library-export/InitializeSearch.png
   :alt: Search for Initialize variable

We'll need to Initialize an Array variable to hold SharePoint Items.

To populate the array, we search for SharePoint connector - **Get Item** action (not *Get Items*!):

|pic4|

.. |pic4| image:: ../images/how-to/list-or-library-export/GetItemSingle.png
   :alt: Search for SharePoint Get Item

You then need to fill out the information about List or Library Source List, and select Item as Item ID:

|pic5|

.. |pic5| image:: ../images/how-to/list-or-library-export/ItemToID.png
   :alt: Dynamic content ID

This will automatically transform SharePoint Get Item action into a part of Apply to Each actions, which will be applied to all Item IDs sent in a request. 

This can be used with Compose action to define certain variables. Search for Compose action and add it inside Apply to Each loop, you can define current SharePoint item variables, such as Amount, Price, Total, etc.

|pic6|

.. |pic6| image:: ../images/how-to/list-or-library-export/ComposeAppend.png
   :alt: Compose and append to array

After getting all the items to the Array, it's now possible to use them in our own actions. In this example, we're using two actions from |Plumsail Documents|.

.. |Plumsail Documents| raw:: html

   <a href="https://plumsail.com/documents/" target="_blank">Plumsail Documents</a>

We'll use |Create HTML from Template|:

.. |Create HTML from Template| raw:: html

   <a href="https://plumsail.com/docs/documents/v1.x/flow/actions/document-processing.html#create-html-from-template" target="_blank">Create HTML from Template</a>

|pic7|

.. |pic7| image:: ../images/how-to/list-or-library-export/htmlTemplate.png
   :alt: Create HTML from Template

And then |Convert HTML to PDF|:

.. |Convert HTML to PDF| raw:: html

   <a href="https://plumsail.com/docs/documents/v1.x/flow/actions/document-processing.html#convert-html-to-pdf" target="_blank">Convert HTML to PDF</a>

|pic8|

.. |pic8| image:: ../images/how-to/list-or-library-export/htmlToPDF.png
   :alt: Convert HTML to PDF

The result of which we'll send as an attachment in an email with **Send an email** action:

|pic9|

.. |pic9| image:: ../images/how-to/list-or-library-export/sendEmail.png
   :alt: Send an email

All we need to do now is save the Flow, and copy the URL from **When a HTTP request is received** action: 

|pic10|

.. |pic10| image:: ../images/how-to/list-or-library-export/copyURL.png
   :alt: Copy URL

Back to our JavaScript editor:

|pic11|

.. |pic11| image:: ../images/how-to/list-or-library-export/JSeditor.png
   :alt: JavaScript editor with new URL


Result
--------------------------------------------------
So, this is how the button looks like on the form, when items are selected:

|pic12|

.. |pic12| image:: ../images/how-to/list-or-library-export/button.png
   :alt: New button on the form

And here's a preview of the PDF received in an email:

|pic13|

.. |pic13| image:: ../images/how-to/list-or-library-export/pdf.png
   :alt: Result PDF