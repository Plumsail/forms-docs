.. title:: Personalized Form sets in Plumsail Forms for SharePoint

.. meta::
   :description: How to create special Form sets, such as a set of forms for supervisors only, and redirect to them based on Azure AD users or groups, SharePoint groups or custom rules

Personalized Form sets in Plumsail Forms for SharePoint
=============================================================

.. contents::
 :local:
 :depth: 1

Form sets allow you to design additional forms for SharePoint - for example, forms for a specific user or group.

|pic1|

.. |pic1| image:: ../images/designer/form-sets/designer-form-sets-addFormSet.png
   :alt: Form sets UI

You can select currently active Form Set in an upper right corner, in the drop-down.
Default Form Set is what all users see if they are not redirected to a custom one.

Add new Form Set by clicking the **+ sign** next to the currently selected Form Set. Clicking the Pen Icon allows you to edit properties of the currently selected Form Set.
Trash bin icon allows you to delete a Form Set. After creating a Form Set, do not forget to save every form you plan to use, such as New, Edit or Display form, or it might be missing.

.. _designer-azurerouting:

Automatic routing based for Azure AD users or groups
-------------------------------------------------------------
When you create a Form Set, straight away, you can configure automatic routing for Azure AD specific users or groups:

|pic-azure|

.. |pic-azure| image:: ../images/designer/form-sets/designer-form-sets-azureADGroups.png
   :alt: Azure AD routing

* Name - the name of the Form Set, can be anything you want, just makes it easier to find among all the Form sets.
* Order - determines the order in which to open Form sets if conditions are met. The lower the Order value, the higher the priority for Form Set to open.
* Add users or groups - select specific users or any Azure AD groups (such Team site groups, for example), to redirect to the Form Set

.. _designer-grouprouting:

Automatic routing based on SharePoint group membership
-------------------------------------------------------------
You can switch to SharePoint groups tab and configure access based on SharePoint groups instead:

|pic-sharepoint|

.. |pic-sharepoint| image:: ../images/designer/form-sets/designer-form-sets-SharePointGroups.png
   :alt: SharePoint group routing

* Name - the name of the Form Set, can be anything you want, just makes it easier to find among all the Form sets.
* Order - determines the order in which to open Form sets if conditions are met. The lower the Order value, the higher the priority for Form Set to open.
* Open forms when a user belongs… - select all groups user must belong to in order to be redirected.
* Excluding the selected groups - completely prevent redirection from these groups, even if users also belong to the groups previously selected.

.. _designer-customrouting:

Custom routing
-------------------------------------------------------------
You are not limited to checking current user's group membership, using custom routing you can use any logic to redirect users to specific form.
With custom routing, you can check current item's field values, user's properties, such as title or department, 
or any other information from SharePoint. Based on this information, you can redirect users to different Form sets or URLs.

Custom routing always takes priority over group routing. So, if your custom code returns ID of a Form Set, 
users will get redirected to the corresponding URL or Form Set all the time, even if they do not belong to the selected groups for this Form Set.
Custom routing is configured for all Forms and Form sets of the current Content Type. Each Content Type has its own custom routing configuration.

.. note::   This can also be used to provide :doc:`different forms for different languages <../how-to/language>`.

To add custom routing conditions, click *Routing* button:

|pic3|

.. |pic3| image:: ../images/designer/form-sets/3-Routing.png
   :alt: Form Routing button

Custom routing is based on JavaScript with SharePoint Patterns & Practices (PnP) |JavaScript Core Library| and 
several predefined variables describing the current context. PnP library contains a fluent API for working with the full SharePoint REST API, 
allowing you to easily get any necessary information from SharePoint.

.. |JavaScript Core Library| raw:: html

   <a href="https://sharepoint.github.io/PnP-JS-Core/" target="_blank">JavaScript Core Library</a>

Some predefined variables accessible from your code:

    -   **webUrl** - URL of the current site
    -   **listId** - ID of the current list
    -   **itemId** - ID of the current item
    -   **pnp** - pnp JS library instance
    -   **web** - current Web from pnp 
    -   **list** - current List from pnp
    -   **item** - current Item from pnp or null for a New form
    -   **host** - check if form is opened in a regular page, in a panel, or in a user web part. Value can be: 0 / 1 / 2. See :ref:`example <designer-hostvar>`.

The code in custom routing must return an ID of a Form Set, or a Promise that is resolved with Form Set ID. 
The ID will be used to render a specific Form Set.

Form Set ID can be found in the lower left corner of the designer, it can be copied with a button click:

|pic4|

.. |pic4| image:: ../images/designer/form-sets/designer-form-sets-id.png
   :alt: Form Set ID

If the code returns nothing or throws an error, default routing is applied. 

You can find examples of custom routing code further below.

Check item's field
**********************************************
Redirect to a certain Form Set if 'Status' field equals 'Solved':

.. code-block:: javascript

    //check if Item already exists, will return true for Edit and Display Form
    if (item) {
        // return Promise
        return item.get()
            .then(function (item) {
                //if Item's Status is Solved, redirect
                if (item.Status == 'Solved') {
                    //return ID of a Form Set
                    return '31fb1f41-63f3-48ff-a1c2-18b4e7f7c3e7'
                }
            });
    }

Check user's property
**********************************************
Redirect to a certain Form Set if User's Department is 'Fire Safety':

.. code-block:: javascript

    //get properties of the current user
    return pnp.sp.profiles.myProperties.get().then(function(result) {
        var props = result.UserProfileProperties;
        //if there is a property with Key: Department and Value: Fire Safety
        if (props.some(function(p){ return p.Key === 'Department' && p.Value === 'Fire Safety'})) {
            //return ID of a Form Set
            return '8720f859-7cca-4c51-8548-7a28f271d6a8';
        }
    });

Check item's Person field
**********************************************
Redirect to a certain Form Set if 'AssignedTo' Person field equals the current user:

.. code-block:: javascript

    //check if Item already exists, will return true for Edit and Display Form
    if (item) {
        //first, get the current user
        var user;
        // return Promise
        return web.currentUser.get()
            .then(function(u) {
                user = u;
                return item.get();
            })
            .then(function(item) {
                //then compare User ID to ID of the user in the AssignedTo field
                if (user.Id == item.AssignedToId) {
                    //return ID of a Form Set
                    return '31fb1f41-63f3-48ff-a1c2-18b4e7f7c3e7';
                }
            });
    }

Check item's multiple selection Person field
**********************************************
Redirect to a certain Form Set if 'People' multiple selection Person field contains the current user:

.. code-block:: javascript

    //check if Item already exists, will return true for Edit and Display Form
    if (item) {
        //first, get the current user
        var user;
        // return Promise
        return web.currentUser.get()
            .then(function(u) {
                user = u;
                return item.get();
            })
            .then(function(item) {
                //if field People contains current user's ID
                if(item.PeopleId && item.PeopleId.indexOf(user.Id) >= 0){
                    //return ID of a Form Set
                    return '8720f859-7cca-4c51-8548-7a28f271d6a8';
                }
            });
    }


.. _designer-hostvar:

Check host
**********************************************
Redirect to a certain Form Set if form is opened in full page mode, in a panel, or in a webpart:

.. code-block:: javascript

    // regular form
    if (host === 0)
        return '568be5c6-383e-4903-ab5b-aeef7f1e76ae';

    // SharePoint panel
    if (host === 1)
        return '87a5e162-3fe5-4459-8527-e1c04e14621f';

    // Plumsail Forms Web Part 
    if (host === 2)
        return '719a0769-1c0a-4a6c-8dcf-57abc8a7d71a';

Practical cases with routing
-----------------------------------------------------
Check out the following examples of how you can use routing in your forms and projects:

   - :doc:`Create forms in multiple languages <../how-to/language>`
   - :doc:`Open edit form by default for a user group <../how-to/edit-form>`
   - :doc:`Personalize form based on user group in SharePoint or Azure AD with Graph API <../how-to/forms-for-groups>`
   - :doc:`Configure a ticket management system <../examples/ticket-management>`
