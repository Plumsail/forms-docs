SP Forms Provision
=========================================

.. contents:: Contents:
 :local:
 :depth: 1

General Info
-------------------------------------------------------------
It is possible to provision forms programmatically using **Plumsail.Forms.Provision** |NuGet package|. 


.. |NuGet package| raw:: html

   <a href="https://www.nuget.org/packages/Plumsail.Forms.Provision/" target="_blank">NuGet package</a>

FormsManager
-------------------------------------------------------------
Forms Manager allows you to manage modern SharePoint Forms for a specific Content Type in the specific List. 
It takes three arguments as parameters: Client Context for SharePoint Site with valid Site Owner credentials, 
the ID of the List, and the ID of the Content Type as a string.

.. code-block:: c#

    var forms = new FormsDesigner.SharePoint.FormsManager(ClientContext ctx, Guid listId, string contenTypeId);

.. list-table::
    :header-rows: 1
    :widths: 10 10 20

    *   -   Parameter
        -   Description
        -   Example

    *   -   **ClientContext ctx**
        -   Client context for the site that you try to access with Full Control Credentials.
        - .. code-block:: c#

                var login = "login@domain.onmicrosoft.com";
                var password = GetSecureString("qwerty");

                var webUrl = "https://domain.sharepoint.com/sites/site";
                var ctx = new ClientContext(webUrl);
                ctx.Credentials = new SharePointOnlineCredentials(login, password);
                
    *   -   **Guid listId**
        -   Guid with ID of the list that you try to access.
        - .. code-block:: c#

                var list = ctx.Web.Lists.GetByTitle("MyList");

                ctx.Load(list);
                ctx.ExecuteQuery();

                var listId = list.Id;
    
    *   -   **string contenTypeId**
        -   String with the Content Type Id
        - .. code-block:: c#

                var cts = list.ContentTypes;

                ctx.Load(cts);
                ctx.ExecuteQuery();

                var contenType = cts.FirstOrDefault(ct => ct.Name == "Item");


FormsManager Methods
-------------------------------------------------------------
Forms Manager has a number of public methods to work with the forms.

.. list-table::
    :header-rows: 1
    :widths: 10 10 20

    *   -   Method
        -   Description
        -   Examples
    *   -   **GenerateForms(Guid formSetId, FormTypes formTypes, XDocument layout, CompiledForm compiledForm)**
        -   Generates specified (New, Edit or Display) form for the specific Form Set. 
            
            Takes 4 arguments - ID of the Form Set(empty Guid for Default), type of the form, layout of the form and the compiled form.
        - .. code-block:: c#

                var layout = XDocument.Load("c:\\provision\\Item_New.xfds");

                var comp = await CompileForm(layout);

                var New = FormsDesigner.Data.SharePoint.FormTypes.New;
                var Edit = FormsDesigner.Data.SharePoint.FormTypes.Edit;
                var Display = FormsDesigner.Data.SharePoint.FormTypes.Display;

                forms.GenerateForms(Guid.Empty, New | Edit | Display, layout, comp);
                
    *   -   **GetFormSets()**
        -   Allows to get form sets for the List. Returns FormSetSettings.
        - .. code-block:: c#

                forms.GetFormSets();

    *   -   **GetLayout(Guid formSetId, FormTypes formType)**
        -   Allows to get specified form's layout from the List for the form set. Can be used instead of exported file.
        - .. code-block:: c#
                
                var typeNew = FormsDesigner.Data.SharePoint.FormTypes.New;
                var typeEdit = FormsDesigner.Data.SharePoint.FormTypes.Edit;
                var typeDisplay = FormsDesigner.Data.SharePoint.FormTypes.Display;

                var layoutNew = forms.GetLayout(Guid.Empty, typeNew);
                var layoutEdit = forms.GetLayout(Guid.Empty, typeEdit);
                var layoutDisplay = forms.GetLayout(Guid.Empty, typeDisplay);
                
    *   -   **ResetForms(Guid formSetId, FormTypes formType)**
        -   Allows to reset the specified form for the specific form set in the List to the default.
        - .. code-block:: c#

                Task.Run(async () =>
                {
                    var typeNew = FormsDesigner.Data.SharePoint.FormTypes.New;
                    // reset the default New Form:
                    forms.ResetForms(Guid.Empty, typeNew);
                }).Wait();
    
    *   -   **SetFormSets(FormSetSettings settings)**
        -   Allows to use FormSetSettings to create a structure for Form Sets in the List. Still need to generate forms after.
        - .. code-block:: c#

                var settings = formsOldSite.GetFormSets();
                formsNewSite.SetFormSets(settings);