Generate a link to form
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Description
--------------------------------------------------
Often, it might be necessary to redirect users to a specific form. It's possible to simply open a form, copy it's link and then use JavaScript for redirection to this specific URL.
But it would also mean that the users are not redirected to a specific Form Set, if you have routing configured, since you bypass the redirection and go directly to page.

Another thing, if the user is not logged in, before reaching the form, they will be redicted to Microsoft's authentication, and in this process, 
the URL would lose its parameters, such as Item ID, preventing the form from opening correctly.

In this article, we're going to show you how you can create general URLs, which would only specify what List and what Item you want to open, 
thus allowing for routing to take place, plus avoiding the lose of parameters during authentication.

Structure
--------------------------------------------------
The structure of the URL is fairly simple:

.. code-block:: javascript

    var url = "https://domain.sharepoint.com/sites/sitename/subsite/_layouts/15/listform.aspx?PageType=" + pageTypeNumber + "&ListId=" + listId + "&ID=" + itemId

* **pageTypeNumber**
    -   a type of the form that you want to open: 
    -   **8** is New Form
    -   **6** is Edit Form 
    -   **4** is Display Form

* **listId** is the ID of the List or Document Library to open, which can be copied from the URL of List/Library settings page:

|pic1|

.. |pic1| image:: ../images/how-to/link-to-form/ListSettingsID.png
   :alt: List ID

* **itemID** is the ID of the Item or Document to open.

Buidling link with JavaScript
--------------------------------------------------
A link can also be built with JavaScript and can be used in variety of situations. To :doc:`redirect user after form submission</how-to/redirect-sp-save>` to the next form, or to :doc:`open form in dialog</javascript/dialog>`, for example.

Use the following code to build link while on a form:

.. code-block:: javascript

    var url = "https://domain.sharepoint.com/sites/site/_layouts/15/listform.aspx";
    //current item's Edit Form URL:
    var params = {
        PageType: 6,
        ListId: fd.spFormCtx.ListAttributes.Id,
        ID: fd.itemId
    }

    url += "?" + $.param(params);
    console.log(url);
    Dialog.open(url);

Now, you don't have to get all these values with JavaScript, some, if not all, can be prepopulated depending on your scenario.