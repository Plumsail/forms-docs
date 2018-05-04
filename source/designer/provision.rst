SP Forms Provision
=========================================

.. contents:: Contents:
 :local:
 :depth: 1

General Info
-------------------------------------------------------------
It is possible to provision forms programmatically using **Plumsail.Forms.Provision** |NuGet package|. 
Find an example of how it can be used in our article - :doc:`Provision Modern UI SharePoint Form</how-to/provision>`.


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
            
            Takes 4 arguments: 
            
            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - type of the form (can be several types separated by *|*).

            **layout** - layout of the form, XDocument from .xfds file.

            **compiledForm** - compiled form.
        - .. code-block:: c#

                var layout = XDocument.Load("c:\\provision\\Item_New.xfds");

                var comp = CompileForm(layout);

                var new = FormsDesigner.Data.SharePoint.FormTypes.New;
                var edit = FormsDesigner.Data.SharePoint.FormTypes.Edit;
                var display = FormsDesigner.Data.SharePoint.FormTypes.Display;

                forms.GenerateForms(Guid.Empty, new | edit | display, layout, comp);
                
    *   -   **GetFormSets()**
        -   Allows to get form sets for the List. Returns FormSetSettings.
        - .. code-block:: c#

                var settings = forms.GetFormSets();

    *   -   **GetLayout(Guid formSetId, FormTypes formType)**
        -   Allows to get specified form's layout from the List for the form set. Can be used instead of exported file.

            Takes 2 arguments:

            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - type of the form (can only be one).
        - .. code-block:: c#
                
                var new = FormsDesigner.Data.SharePoint.FormTypes.New;
                var edit = FormsDesigner.Data.SharePoint.FormTypes.Edit;
                var display = FormsDesigner.Data.SharePoint.FormTypes.Display;

                var layoutNew = forms.GetLayout(Guid.Empty, new);
                var layoutEdit = forms.GetLayout(Guid.Empty, edit);
                var layoutDisplay = forms.GetLayout(Guid.Empty, display);
                
    *   -   **ResetForms(Guid formSetId, FormTypes formType)**
        -   Allows to reset the specified form for the specific form set in the List to the default.
        
            Takes 2 arguments: 
            
            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - type of the form (can be several types separated by *|*).
        - .. code-block:: c#

                var new = FormsDesigner.Data.SharePoint.FormTypes.New;
                // reset the default New Form:
                forms.ResetForms(Guid.Empty, new);
    
    *   -   **SetFormSets(FormSetSettings settings)**
        -   Allows to use FormSetSettings to create a structure for Form Sets in the List. Still need to generate forms after.

            Takes 1 arguments: 
            
            **settings** - settings for routing, including rules and logic.
        - .. code-block:: c#

                var settings = formsOldSite.GetFormSets();
                formsNewSite.SetFormSets(settings);

FormSetSettings
-------------------------------------------------------------
FormSetSettings can be retrieved with **GetFormSets()** and set with **SetFormSets(FormSetSettings)**. 
These settings contain code for :ref:`designer-customrouting`, as well as information about Form Sets, including groups used for redirection.

.. list-table::
    :header-rows: 1
    :widths: 10 10 20

    *   -   Properties
        -   Description
        -   Examples
    *   -   **CustomRouting**
        -   Contains string with logic for custom routing. Can be used to get and set. 
        - .. code-block:: c#

                var fss = forms.GetFormSets();
                var routing = fss.CustomRouting;
    *   -   **FormSets**
        -   Contains IEnumerable of Form Sets. Can be used to get and set. 

            Returned Form Sets contain:

            **ExcludedGroupIds** - IEnumerable of excl. group IDs (ints).

            **IncludedGroupIds** - IEnumerable of incl. group IDs (ints).

            **Order** - int order of the form set.

            **Title** - string title of the form set.

            **Id** - guid formSetId, can be used with *GenerateForms()*, *GetLayout()*, etc. 
        - .. code-block:: c#

                var fss = forms.GetFormSets();
                var sets = fss.FormSets;

                foreach (var Set in sets)
                {
                    var exclude = Set.ExcludedGroupIds;
                    var include = Set.IncludedGroupIds;
                    var order = Set.Order;
                    var title = Set.Title;
                    var guid = Set.Id;
                }