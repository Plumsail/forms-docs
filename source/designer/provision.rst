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

Here's an example of FormsManager initialization:

.. code-block:: c#

    using FormsDesigner.Data;
    using Microsoft.SharePoint.Client;
    using System;
    using System.Linq;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using System.Security;
    using System.Threading.Tasks;
    using System.Xml.Linq;
       
    namespace ProvisionApp
    {
        class Program
        {
            static void Main()
            {
                // SharePoint login and password for the site:
                var login = "your-login@your-domain.onmicrosoft.com";W

                Console.WriteLine("Please enter the password:");
                var passwordString = Console.ReadLine();
                var password = GetSecureString(passwordString);

                // URL of the site:
                var webUrl = "https://your-domain.sharepoint.com/sites/your-site";

                using (var ctx = new ClientContext(webUrl))
                {
                    ctx.Credentials = new SharePointOnlineCredentials(login, password);

                    // List:
                    var list = ctx.Web.Lists.GetByTitle("MyList");
                    var cts = list.ContentTypes;

                    ctx.Load(list);
                    ctx.Load(cts);
                    ctx.ExecuteQuery();

                    // Content Type:
                    var contenType = cts.FirstOrDefault(ct => ct.Name == "Item");

                    //FormsManager created:
                    var forms = new FormsDesigner.SharePoint.FormsManager(ctx, list.Id, contenType.Id.ToString());

                    /*
                        the rest of the code goes here...
                    */
                }
            }

            private static SecureString GetSecureString(string s)
            {
                SecureString result = new SecureString();
                foreach (char c in s.ToCharArray())
                {
                    result.AppendChar(c);
                }

                return result;
            }
        }
    }

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

                // Load your XFDS-files:
                var layoutNew = XDocument.Load("c:\\provision\\Item_New.xfds");
                var layoutEdit = XDocument.Load("c:\\provision\\Item_Edit.xfds");
                var layoutDisplay = XDocument.Load("c:\\provision\\Item_Display.xfds");

                Task.Run(async () =>
                {
                    var compFormNew = await CompileForm(layoutNew);
                    var compFormEdit = await CompileForm(layoutEdit);
                    var compFormDisplay = await CompileForm(layoutDisplay);

                    var typeNew = FormsDesigner.Data.SharePoint.FormTypes.New;
                    var typeEdit = FormsDesigner.Data.SharePoint.FormTypes.Edit;
                    var typeDisplay = FormsDesigner.Data.SharePoint.FormTypes.Display;

                    forms.GenerateForms(Guid.Empty, typeNew, layoutNew, compFormNew);
                    forms.GenerateForms(Guid.Empty, typeEdit, layoutEdit, compFormEdit);
                    forms.GenerateForms(Guid.Empty, typeDisplay, layoutDisplay, compFormDisplay);
                }).Wait();
                
    *   -   **GetFormSets()**
        -   Allows to get form sets for the List. Returns FormSetSettings.
        - .. code-block:: c#

                forms.GetFormSets;

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

                var settings = formsOldSite.GetFormSets
                formsNewSite.SetFormSets(settings);