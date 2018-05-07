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

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Constructor
        -   Description/Examples

    *   -   **FormsManager(ClientContext ctx, Guid listId, string contenTypeId);**
        -   Forms Manager allows you to manage modern SharePoint Forms for a specific Content Type in the specific List. 
            It takes three arguments as parameters: Client Context for SharePoint Site with valid Site Owner credentials, 
            the ID of the List, and the ID of the Content Type as a string.

            **ctx** - client context for the site that you try to access, with Full Control Credentials.

            **listId** - ID of the list that you try to access.

            **contentTypeId** - string with the Content Type Id.
            
            |

            *Example:*
            
            .. code-block:: c#

                static void Main()
                {
                    // SharePoint Login:
                    var login = "your-login@your-domain.onmicrosoft.com";
                    // Login's Password:
                    var password = GetSecureString("qwerty");
                    // List Title:
                    var listTitle = "LookupTest";
                    // Content Type Name:
                    var contentType = "Item";
                    // Path to the exported form:
                    var formPath = "c:\\provision\\Item_Edit.xfds";
                    // URL of the site:
                    var webUrl = "https://your-domain.sharepoint.com/sites/your-site";

                    using (var ctx = new ClientContext(webUrl))
                    {
                        ctx.Credentials = new SharePointOnlineCredentials(login, password);

                        var list = ctx.Web.Lists.GetByTitle(listTitle);
                        var cts = list.ContentTypes;

                        ctx.Load(list);
                        ctx.Load(cts);
                        ctx.ExecuteQuery();

                        var cType = cts.FirstOrDefault(ct => ct.Name == contentType);
                        var cId = cType.Id.ToString();

                        var forms = 
                            new FormsDesigner.SharePoint.FormsManager(ctx, list.Id, cId);
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


FormsManager Methods
-------------------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Method
        -   Description/Examples   
    *   -   **GenerateForms(Guid formSetId, FormTypes formTypes, XDocument layout, CompiledForm compiledForm)**
        -   Generates specified (New, Edit or Display) form for the specific Form Set. 
            
            Takes 4 arguments: 
            
            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - Flags indicating one or more form types.

            **layout** - layout of the form, XDocument from .xfds file.

            **compiledForm** - compiled form.
            
            |

            *Example:*
            
            .. code-block:: c#

                var layout = XDocument.Load("c:\\provision\\Item_New.xfds");

                var comp = CompileForm(layout);

                var new = FormsDesigner.Data.SharePoint.FormTypes.New;
                var edit = FormsDesigner.Data.SharePoint.FormTypes.Edit;
                var display = FormsDesigner.Data.SharePoint.FormTypes.Display;

                forms.GenerateForms(Guid.Empty, new | edit | display, layout, comp);
                
    *   -   **GetFormSets()**
        -   Allows to get form sets for the List. Returns :ref:`designer-formsetsettings`.

            |

            *Example:*
            
            .. code-block:: c#

                var settings = forms.GetFormSets();

    *   -   **GetLayout(Guid formSetId, FormTypes formType)**
        -   Allows to get specified form's layout from the List for the form set. The layout can be used with *GenerateForms()* method, 
            instead of getting layout fromexported file.

            Takes 2 arguments:

            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - a Flag indicating one form type.
            
            |

            *Example:*

            .. code-block:: c#
                
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

            **formTypes** - Flags indicating one or more form types.
            
            |

            *Example:*

            .. code-block:: c#

                var new = FormsDesigner.Data.SharePoint.FormTypes.New;
                // reset the default New Form:
                forms.ResetForms(Guid.Empty, new);
    
    *   -   **SetFormSets(FormSetSettings settings)**
        -   Allows to use FormSetSettings to create a structure for Form Sets in the List. Still need to generate forms after.

            Takes 1 arguments: 
            
            **settings** - settings for routing, including rules and logic.
            
            |

            *Example:*
            
            .. code-block:: c#

                var settings = formsOldSite.GetFormSets();
                formsNewSite.SetFormSets(settings);

.. _designer-formsetsettings:

FormSetSettings
-------------------------------------------------------------
FormSetSettings can be retrieved with **GetFormSets()** and set with **SetFormSets(FormSetSettings)**. 

These settings contain code for :ref:`designer-customrouting`, as well as information about Form Sets, including groups used for redirection.

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Properties
        -   Description/Examples
    *   -   **CustomRouting**
        -   Contains string with logic for custom routing. Can be used to get and set.
            
            |

            *Example:*
            
            .. code-block:: c#

                var fss = forms.GetFormSets();
                var routing = fss.CustomRouting;
    *   -   **FormSets**
        -   Contains IEnumerable of Form Sets. Can be used to get and set. 

            Returned Form Set class contains:

            **ExcludedGroupIds** - IEnumerable of excl. group IDs (ints).

            **IncludedGroupIds** - IEnumerable of incl. group IDs (ints).

            **Order** - int order of the form set.

            **Title** - string title of the form set.

            **Id** - guid formSetId, can be used with *GenerateForms()*, *GetLayout()*, etc.
            
            |

            *Example:*
            
            .. code-block:: c#

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