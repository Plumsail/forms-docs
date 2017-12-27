Convert DataTable into HTML template
===========================================================
This article will describe how you can convert :ref:`designer-datatable` into HTML template with |Plumsail Actions|.

You can simply convert DataTable into HTML table with *Data Operations - Create HTML table* actions in MS Flow, 
this step is described in :ref:`flow-html-table` article. 

But this operation comes with limitation, primarily, you can't affect values stored in the table and the way they are displayed.

For example, you can't convert dates to a more readable format or add a dollar sign to number columns. In this article, we will do just that.

Setting up the form
--------------------------------------------------
We will use the same form that we used in the previous article - :ref:`data-table-form`.

It's still the same Expense Reimbursement Form, we just need to add Date column to our Expenses table and set its type to Date:

.. image:: ../images/how-to/data-table-convert-html/1_Add_Date.png
   :alt: Add Date column to Expenses table

|

Now, this can be it, but we can go one step beyond and ensure that dates included in the table will be in the range between our *From* and *To* date fields:

.. image:: ../images/how-to/data-table-convert-html/2_Error.png
   :alt: Expense Dates must be between To and From

|

This is an optional step, but it can be easily achieved by adding this code to our fd.rendered() event:

.. code-block:: javascript

    fd.rendered(function(){
        //... all the previous code
        
        fd.control('ExpensesTable').addValidator({
            error: 'Expenses should be in the period between From and To',
            validate: function(value) {
                for (var i = 0; i < value.length; i++){
                    if (value[i].Date <= fd.field('From').value) {
                        return false;
                    }
                    else if (value[i].Date >= fd.field('To').value) {
                        return false;
                    }			
                }
                
                return true;
            }
        });
    });

Now we can start working on our Flow.

Fixing time zones for Dates
****************************************
One issue that you may face with the dates in Flow is time zone offset. 

Dates in Microsoft Flow are in Universal Time (aka, UTC or GMT) by default, but Plumsail Forms dates are in your local time which could lead to unexpected results.

These differences can be solved by adjusting dates before submission with JavaScript in **fd.beforeSave()** event.

In our case, we can make sure that dates are correct with the following code, including dates in our expenses table:

.. code-block:: javascript

    fd.beforeSave(function(data) {
        data.From = new Date(data.From.getTime() 
            - data.From.getTimezoneOffset() * 60000);
        data.To = new Date(data.To.getTime() 
            - data.To.getTimezoneOffset() * 60000);
        for (var i = 0; i < data.ExpensesTable.length; i++){
		    var date = data.ExpensesTable[i].Date;
		    data.ExpensesTable[i].Date = new Date(date.getTime() 
			    - date.getTimezoneOffset() * 60000);
	    }
    });


Microsoft Flow using HTML template functionality
--------------------------------------------------
This will show you how you can set up MS Flow with DataTable without converting it to HTML table first.

In this example, we will also use |Plumsail Actions| to create HTML with template which would use submitted data, 
then convert this HTML into PDF, and we will rely on Plumsail Actions even more.

If you haven't read our introduction to using MS Flow with Plumsail Forms, you can find information on how to add our custom connector :doc:`here </microsoftFlow>`.

Plumsail Actions
************************************************

For us to create HTML template from our Form, we don't even need to include *Data Operations - Parse JSON* Action, but you can include it if you plan to use individual fields anywhere else in your Flow.

All we need is to subscribe to the submission of the correct form with Plumsail Forms trigger by copying Form ID inside *Form is submitted* trigger:

.. image:: /images/flow/11_FormID.png
   :alt: Form ID

|

We will use Plumsail Actions connector straight away, which you can read about setting up |Plumsail Actions connector|. 

You can either create Custom connector or use MS Flow Premium connector, 
but you will need to have an API key from |Plumsail Account| in both cases.

.. |Plumsail Account| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank">Plumsail Account</a>

.. |Plumsail Actions connector| raw:: html

   <a href="https://plumsail.com/docs/actions/v1.x/getting-started/use-from-flow.html" target="_blank">here</a>

Once the connector is set up, search for HTML Template and select *Plumsail Documents - Create HTML from template*:

.. image:: ../images/how-to/data-table-flow/4_Plumsail_Documents_Search.png
   :alt: Search for HTML Template and select Plumsail Documents - Create HTML from template

| 

Once the action is added, we need to fill in both *Source HTML* and *Template Data*. 

Since *Source HTML* uses *Template Data* quite extensively, it's best to first define *Template Data*.

*Template Data* needs to be composed as a JavaScript object where we include all our data, in our case - just the form.

First, I'll create very basic structure for our object:

.. code-block:: javascript

    {
        "Form": INSERT FORM HERE
    }

Now, we can insert Form Body inside "Form":

.. image:: ../images/how-to/data-table-convert-html/3_HTML_Template_Form.png
   :alt: HTML Template data with Form

| 

And that's it! We don't need anything else in the template as we can access all our data from the submitted form.

Now we can write Source HTML and use our Template data to populate it. We can also include style with it by either linking HTML to CSS file or just include style tag inside Source HTML. 
Even JavaScript can be included and it will be executed unless it's asynchronous.

Here's an HTML that I've used:

.. code-block:: HTML

    <!doctype html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>Expense Reimbursement Request</title>
        <style>
            body {font-family:Arial, Helvetica, sans-serif;}
            table {border-collapse: collapse; width: 100%; }
            table, th, td {border: 1px solid slategray; margin: 5px;}
            .signature { display: inline; width: 30% }
        </style>
    </head>
    <body>
        <h1>Expense Reimbursement Request</h1>
        <p>Name: {{Form.Name}}</p>
        <p>Department: {{Form.Department}}</p>
        <p>Business Purpose: {{Form.Purpose}}</p>
        <p>From: {{Form.From:d}} To: {{Form.To:d}} </p>
        <h2>Table of expenses:</h2>
    <table>
        <tr>
            <th>Description</th>
            <th>Category</th> 
            <th>Cost</th>
            <th>Date</th>
        </tr>
        {{#each Form.ExpensesTable}}
        <tr>
            <td>{{Description}}</td>
            <td>{{Category}}</td> 
            <td>${{Cost}}</td>
            <td>{{Date:d}}</td>
        </tr>
        {{/each}}
    </table>
        <h3>Total: {{Form.Total}}</h3>
        <div class="signature">
            <h4>Signature:</h4>
            <img src="{{Form.Signature}}">
        </div>
    </body>
    </html>

As you can see, there are several interesting things I've used here. First of all, I've formatted the dates like this:

.. code-block:: HTML

    <p>From: {{Form.From:d}} To: {{Form.To:d}} </p>

Adding **:d** after date will automatically convert any date to American Short Date format *MM/dd/yyyy*.

Plumsail Actions HTML Template engine is based on |mustache#| and provides the same formatting based on |String.Format|.

Another thing of interest is iteration through each item in ExpensesTable:

.. code-block:: HTML

        {{#each Form.ExpensesTable}}
        <tr>
            <td>{{Description}}</td>
            <td>{{Category}}</td> 
            <td>${{Cost}}</td>
            <td>{{Date:d}}</td>
        </tr>
        {{/each}}

Since ExpensesTable is passed as an array of objects, it's really easy to do, and then I can also access various columns inside {{#each}}{{/each}}.

As you can see, I've formatted the dates and added a dollar sign before cost, to make result more readable and easier to understand.

*   **Note:** *While formatting with String.Format is very easy, it happens on the server and the server automatically converts everything to en-US culture*.
    
    *If you want to format your values to a different culture, you can either do it ouside HTML Template engine or use JavaScript which is also executed when HTML template is created*.

.. |mustache#| raw:: html

   <a href="https://github.com/jehugaleahsa/mustache-sharp" target="_blank">mustache#</a>

.. |String.Format| raw:: html

   <a href="https://msdn.microsoft.com/en-us/library/system.string.format.aspx" target="_blank">String.Format</a>

.. |Plumsail Actions| raw:: html

   <a href="https://plumsail.com/actions/" target="_blank">Plumsail Actions</a>

Now we can convert result HTML into PDF. Search for Plumsail Documents and select *Plumsail Documents - Convert HTML to PDF*:

.. image:: ../images/how-to/data-table-flow/6_Plumsail_Documents_Search2.png
   :alt: Search for Plumsail Documents and select Plumsail Documents - Convert HTML to PDF

| 

Place Result HTML from the last action inside Source HTML field:

.. image:: ../images/how-to/data-table-flow/7_Plumsail_Convert_HTML_to_PDF.png
   :alt: Plumsail Documents - Convert HTML to PDF

| 

Read more on how to receive this PDF via email in :ref:`email-pdf-attachment` section.

And here's PDF that I receive from Flow:

.. image:: ../images/how-to/data-table-convert-html/4_PDF.png
   :alt: Final PDF

| 