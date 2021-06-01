.. title:: Sharing web forms created with Plumsail Forms

.. meta::
   :description: There are two main ways to ensure that your forms reach the end user - share form via a link or publish it to a webpage on your site

Sharing web forms created with Plumsail Forms
==================================================

.. contents::
 :local:
 :depth: 2

Sharing pages
-------------------------------------------------------------
Sharing pages allow you to share forms directly with users - via the URL. You can send this URL in an email, or add it to any link on your site.

To create a sharing page, please, go to your Plumsail Account → Forms → Pages section and click **Add page**:

|pic1|

.. |pic1| image:: /images/start/sharing-add-page.png
   :alt: Add page for sharing

Once you click it, you'll be greeted with the following screen:

|pic2|

.. |pic2| image:: /images/start/sharing-new-page.png
   :alt: New page creation

Here, you can configure sharing page to your liking and change its appearance to match your company's or personal style.

If you select **Make default** for this page, you'll be able to share any form with this page, by copying links in |Forms section| of your account:

.. |Forms section| raw:: html

   <a href="https://plumsail.com/forms/forms/" target="_blank">Forms section</a>

|pic3|

.. |pic3| image:: /images/start/sharing-forms-links.png
   :alt: Links to forms

**Title** field is mandatory and its required to identify each sharing page that you have. You can also change the **Logo** and add a link to it, so when users click on the logo, it redirects them to your site. Adjust **Header** where the logo is placed by switching header color or the pattern, where you can choose from many options. Choose **Body background** - either a solid color or an image.

You can upload your own image or select one of existing in image gallery:

|pic8|

.. |pic8| image:: /images/start/sharing-background-gallery.png
   :alt: Background image gallery

Customize the text that appears above the form.

Finally, you can also adjust **Footer**'s background color, text color and what text will appear in the footer.

With all that done, save the page.

After saving you'll get some extra options. For once, you'll be able to **Save as** or **Delete** the page. You'll also finally get an option to **Share** the page:

|pic13|

.. |pic13| image:: /images/start/sharing-share-quit.png
   :alt: Share or quit
   
When you click **Share**, you'll be able to choose which form to share and copy the URL for sharing:

|pic14|

.. |pic14| image:: /images/start/sharing-select-form.png
   :alt: Select form for sharing and copy its URL

And here's the page that I've created in just a couple of minutes with a simple form:

|pic15|

.. |pic15| image:: /images/start/sharing-page-result.png
   :alt: Final page

.. note:: To actually work with the data, please, check out our :doc:`Collecting data from submissions </submissions>` article, or read about handling data in :doc:`MS Power Automate </microsoft-flow>` or :doc:`Zapier </zapier>`.

Embedding forms
-------------------------------------------------------------

Wix
**********************************
|Wix|

Powerful website building platform with lots of templates to choose from. Find out how you can embed forms on your :doc:`Wix website </embed/wix>`.

.. |Wix| image:: ./images/embed/wix/embed-wix-logo.png
   :alt: Wix logo

Squarespace
**********************************
|Squarespace|

All-in-one solution for anyone looking to create a beautiful website. Find out how you can embed forms on your :doc:`Squarespace website </embed/squarespace>`.

.. |Squarespace| image:: ./images/embed/squarespace/embed-squarespace-logo.png
   :alt: Squarespace logo

Joomla!
**********************************
|Joomla!|

A free and open-source content management system for publishing web content. Find out how you can embed forms on your :doc:`Joomla! website </embed/joomla>`.

.. |Joomla!| image:: ./images/embed/joomla/embed-joomla-logo.png
   :alt: Joomla! logo

Facebook
**********************************
|Facebook|

One of the most used social media platforms in the world. Find out how you can embed forms on your :doc:`Facebook page </embed/facebook>`.

.. |Facebook| image:: ./images/embed/facebook/embed-facebook-logo.png
   :alt: Facebook logo

Custom web site
**********************************

You can publish Public Web Form to any webpage on your own site or anywhere else on the web, where you can edit the HTML and add our widget.

The widget can be found in Sharing Settings in the designer where you can copy it to clipboard:

|pic18|

.. |pic18| image:: ./images/start/start-copy-snippet.png
   :alt: Copy Form Widget snippet in Sharing Settings

After copying the widget, simply insert it as HTML to your page and the form will be published, ready to receive submissions:

|pic20|

.. |pic20| image:: ./images/start/form-published.png
   :alt: Public Web Form Published

If you're placing more than one form per page, make sure to change *div id=*"**plumsail-form**" and *new Plumsail.Form(*"**#plumsail-form**" to something unique for each widget. The easiest option is to add an index, for example:

.. code-block:: HTML

   <script type="text/javascript" src="https://forms.plumsail.com/widget/***/app.js"></script>
   <div id="plumsail-form1"><div class="fd-form-loading"></div></div>
   <script type="text/javascript">
      var fd = new Plumsail.Form("#plumsail-form1", "...");
   </script>

   <script type="text/javascript" src="https://forms.plumsail.com/widget/***/app.js"></script>
   <div id="plumsail-form2"><div class="fd-form-loading"></div></div>
   <script type="text/javascript">
      var fd = new Plumsail.Form("#plumsail-form2", "...");
   </script>

Access management
-------------------------------------------------------------
Normally, a web form can be completed and submitted by anyone, but you can require users to authenticate via Microsoft Account:

|auth_pic|

.. |auth_pic| image:: /images/authorization/authorization-domain.png
   :alt: Restrict to a domain

Here you can configure the following options:

- Enable access to authenticated users only
- Allow users to submit the form just once
- Allow users to edit their submissions
- Provide access to the form to specific Microsoft 365 groups or users

Find more in :doc:`Authorization for public web forms </authorization>`.
