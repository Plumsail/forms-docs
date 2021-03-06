.. title:: Redirect users after submitting a SharePoint form

.. meta::
   :description: Use JavaScript to redirect users to another form or specific URL after saving the changes to current item

How to redirect users to another form or specific URL after submitting a SharePoint form
=========================================================================================

Working with SharePoint, it's often important to guide users through the process of creating, editing and even of viewing items and documents. You may want to redirect users to some page on the site or a different form. How can this be done?

Nothing could be simpler actually as you will find in this article. With the use of the **spSaved()** event, it can be done with very little code. Read more about different events in our :ref:`js-events` section.

.. Note:: The examples below are not applicable when the form is opened in a panel. RedirectUrl is ignored inside a panel.

.. contents::
 :local:
 :depth: 1

Redirect to any page
--------------------------------------------------
To redirect users to any page on the web, all you need to know is the URL of this page. It can be a page on your SharePoint site or it can be any website page. 

Just add this code to JavaScript editor and it will automatically redirect users to the specified page:

.. code-block:: javascript

    fd.spSaved(function(result) {
        //simply replace this URL with yours:
        result.RedirectUrl = 
            "https://domain.sharepoint.com/sites/sitename/SitePages/ThankYou.aspx";
    });

Redirect to New Form
--------------------------------------------------
Do you want your users to be able to start working on a new item straight after they save an item? That's possible by redirecting them to the New Form of the same list as soon as the form is saved.

This code redirects users to the New Form and can work from both New Form and Edit Form:

.. code-block:: javascript

    fd.spSaved(function(result) {
        var listId = fd.spFormCtx.ListAttributes.Id;

        //replace "https://domain.sharepoint.com/sites/sitename/subsite" with path to your site
        //PageType=8 means New Form, no itemId is required
        result.RedirectUrl = 
            "https://domain.sharepoint.com/sites/sitename/subsite/_layouts/15/listform.aspx?PageType=8&ListId="
            + listId;
    });

Redirect to Edit Form
--------------------------------------------------
Sometimes, it's important to redirect users to Edit Form. For example, you want users to save an item and still be able to continue editing it. The best option in this case would be redirect users seamlessly from the New Form to the Edit Form, once they click the save button.

This code will do just that:

.. code-block:: javascript

    fd.spSaved(function(result) {
        var listId = fd.spFormCtx.ListAttributes.Id;
        var itemId = result.Id;

        //replace "https://domain.sharepoint.com/sites/sitename/subsite" with path to your site
        //PageType=6 means Edit Form
        result.RedirectUrl = 
            "https://domain.sharepoint.com/sites/sitename/subsite/_layouts/15/listform.aspx?PageType=6&ListId=" 
            + listId + "&ID=" + itemId;
    });

Prevent redirection on save
--------------------------------------------------
For Edit Form, it is possible to use code which will prevent redirection on save, so you can save the form and continue working.

*Please, do not use for New Form! Redirect to Edit Form instead!*

.. code-block:: javascript

    fd.spSaved(function(result) {
        result.RedirectUrl = null;
    });

Redirect to Display Form
--------------------------------------------------
Finally, you can also redirect users to the Display Form, from both the New Form and the Edit Form.

Here's how it can be done:

.. code-block:: javascript

    fd.spSaved(function(result) {
        var listId = fd.spFormCtx.ListAttributes.Id
        var itemId = result.Id;

        //replace "https://domain.sharepoint.com/sites/sitename/subsite" with path to your site
        //PageType=4 means Display Form
        result.RedirectUrl = 
            "https://domain.sharepoint.com/sites/sitename/subsite/_layouts/15/listform.aspx?PageType=4&ListId="
            + listId + "&ID=" + itemId;
    });