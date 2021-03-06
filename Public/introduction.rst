.. title:: Introduction to building online forms with Plumsail Forms

.. meta::
   :description: Design and publish elegant, responsive and highly customizable forms to any web page by simply adding an HTML widget to it, or share it via a link.

Introduction to building online forms with Plumsail Forms
===============================================================
Plumsail Forms allow you to design and publish elegant, responsive and highly customizable forms to any web page by simply adding an HTML widget to it, or share it via a link.
When user submits the form, all data is handled by :doc:`Power Automate (MS Flow) </microsoft-flow>` which opens an ocean of possibilities for its use.
The data is collected from anonymous users and can be protected with |reCAPTCHA| to prevent Spam submissions.

.. |reCAPTCHA| raw:: html

   <a href="https://www.google.com/recaptcha" target="_blank">reCAPTCHA</a>

If you are looking for a way to easily design custom forms and apply complex logic to them, but at the same time allow anonymous users to submit data, 
which you can then add to SharePoint Lists, Excel documents, Google sheets or SQL database, and do much more with it, then Plumsail Forms is for you.

      .. toctree::
            :caption: First Steps
            :maxdepth: 1

            ./installation
            ./design
            ./microsoft-flow
            ./zapier
            ./licensing
 
Complex business forms made simple
--------------------------------------------------
While many products on the market offer tools to build custom forms, very few can boast the same level of interactivity as Plumsail Forms. 
Our forms offer a large variety of fields and controls to be placed on the form, 
such as Data Table which allows users to fill out an Excel-like table, or Ink Sketch which allows hand signatures or drawings to be submitted.
We also support Attachments, so your users can even upload files through the form.

More than that, the forms are responsive and scale well for all screen sizes. 
You can also easily customize phone and tablet layouts to make them even more accessible to users on mobile devices.
Custom containers such as Tabs and Accordions allow you to logically separate form into parts.

Finally, our JavaScript API will allow you to do even the most complex actions and calculations with the form.
Automatically calculate field values, such as Total Value or Due Date, validate field values before submission,
customize, hide or show certain elements on the form depending on your needs and much more.

Plumsail Forms are built using |Bootstrap| and |Vue| and as such are very light, responsive and easy to customize, 
while offering an enormous potential for customization. Read more about :doc:`designing your first form </design>`.

Share the form or publish anywhere
--------------------------------------------------
Gone are the limitations - now :doc:`you have options </sharing>`: share forms via the URL or publish the form to any page.

If you can customize HTML of the web page, you can publish the web form. 
It can be your company's public site where clients would be able to fill out the form,
or it can be a private site where all users need to be authorized first. 
It can even be a public repository, such as Codepen, you can still publish the form.

As long as your user has an internet connection, the form will be submitted to :doc:`Power Automate (MS Flow) </microsoft-flow>` or :doc:`Zapier </zapier>`. If there is no connection,
user will be notified with an error message and the data will be stored in the browser's session storage. 
As soon as connection is restored, user will be able to submit the form again with the same data.

Data submitted and handled
--------------------------------------------------
The easiest option to handle data is to store submissions in your Plumsail Account, find out how to do it in our :doc:`Collecting data from submissions </submissions>` article.

Alternatively, :doc:`MS Power Automate (MS Flow) </microsoft-flow>` is a cloud-based automation tool which offers a huge number of potential operations and you can use it to your advantage.
So, the forms are submitted to Power Automate, but what can be done with the data? The amount of actions is constantly growing, so we won't be able to
cover all the use cases even if we tried, but our documentation contains some of the most popular examples.

For starters, you can :doc:`Send an email with Outlook </how-to/email>`, or :doc:`create Items in SharePoint List </how-to/item>`, 
:doc:`upload files to SharePoint Library </how-to/file>` (or Box, or Dropbox, etc.), :doc:`add records to SQL server </how-to/sql>`, 
:doc:`or Excel file, or Google Sheets </how-to/excel-single-row>`. Much more is possible and we'll continue updating our documentation to include more 
interesting cases which you would be able to incorporate in your Flows.

We also fully support :doc:`Zapier </zapier>`.

Find out :doc:`how to install the product </installation>`.

.. |Bootstrap| raw:: html

   <a href="https://getbootstrap.com/" target="_blank">Bootstrap 4</a>

.. |Vue| raw:: html

   <a href="https://vuejs.org/" target="_blank">Vue.js 2</a>