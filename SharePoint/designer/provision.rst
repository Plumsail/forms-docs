SharePoint Forms Provision
=========================================

.. contents:: Contents:
 :local:
 :depth: 1

General Info
-------------------------------------------------------------
It is possible to provision forms programmatically using **Plumsail.Forms.O365** |NuGet package|. 

.. important:: For SharePoint 2019, please, use the **Plumsail.Forms.SP2019** |NuGet package 2019| instead. 

In order to use the package, you need to have *.NET Framework v.4.5.2* or higher installed.

Find an example of how it can be used in our article - :doc:`Provision Modern UI SharePoint Form</how-to/provision>`.

.. |NuGet package| raw:: html

   <a href="https://www.nuget.org/packages/Plumsail.Forms.O365" target="_blank">NuGet package</a>

.. |NuGet package 2019| raw:: html

   <a href="https://www.nuget.org/packages/Plumsail.Forms.SP2019/" target="_blank">NuGet package</a>


FormsManager
-------------------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Constructor
        -   Description/Examples

    *   -   **FormsManager(ClientContext ctx, Guid listId, string contentTypeId);**
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

                        var forms = new FormsManager(ctx, list.Id, cId);

                        //use FormsManager methods here...
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
    *   -   **GenerateForms(Guid formSetId, FormTypes formTypes, XDocument layout)**
        -   Generates specified (New, Edit or Display) form for the specific Form Set. 
            
            Takes 3 arguments: 
            
            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - Flags indicating one or more form types.

            **layout** - layout of the form, XDocument from .xfds file.
            
            |

            *Example:*
            
            .. code-block:: c#

                var layout = XDocument.Load("c:\\provision\\Item_New.xfds");

                forms.GenerateForms(
                        Guid.Empty, 
                        FormTypes.New | FormTypes.Edit | FormTypes.Display, 
                        layout);
                
    *   -   **GetFormSets()**
        -   Allows to get form sets for the List. Returns :ref:`designer-formsetsettings`.

            .. important:: Only available after customization of Form Sets, for example, adding new Form Set or customizing the Panel.

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
                
                var layoutNew = forms.GetLayout(Guid.Empty, FormTypes.New);
                var layoutEdit = forms.GetLayout(Guid.Empty, FormTypes.Edit);
                var layoutDisplay = forms.GetLayout(Guid.Empty, FormTypes.Display);
                
    *   -   **ResetForms(Guid formSetId, FormTypes formType)**
        -   Allows to reset the specified form for the specific form set in the List to the default.
        
            Takes 2 arguments: 
            
            **formSetId** - ID of the Form Set(empty Guid for Default).

            **formTypes** - Flags indicating one or more form types.
            
            |

            *Example:*

            .. code-block:: c#

                // reset the default New Form:
                forms.ResetForms(Guid.Empty, FormTypes.New);
    
    *   -   **SetFormSets(FormSetSettings settings)**
        -   Allows to use FormSetSettings to create a structure for Form Sets in the List. Still need to generate forms after.

            Takes 1 arguments: 
            
            **settings** - settings for routing, including rules and logic.
            
            |

            *Example:*
            
            .. code-block:: c#

                var settings = formsOldSite.GetFormSets();
                formsNewSite.SetFormSets(settings);

                //alternatively create new Form Set settings
                formsNewSite.SetFormSets(new FormsDesigner.Data.SharePoint.FormSetSettings() {
                    //use Constructor to set properties
                })

.. _designer-formsetsettings:

FormSetSettings
-------------------------------------------------------------
FormSetSettings can be retrieved with **GetFormSets()** and set with **SetFormSets(FormSetSettings)**. 

These settings contain code for :ref:`designer-customrouting`, as well as information about Form Sets, including groups used for redirection.

For examples of working with Form Sets, please, check out :doc:`Working with Form Sets when Provisioning</how-to/provision-fs>`.

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

    *   -   **AddListViewCommands**
        -   Contains boolean that determines if Form Commands (Form Panel) are loaded in the list views. Can be used to get and set.

            If set to false, neither **Panel** nor **CustomListViewCode** properties will work.
            
            |

            *Example:*
            
            .. code-block:: c#

                var fss = forms.GetFormSets();
                fss.AddListViewCommands = true;
            
    *   -   **Panel**
        -   Contains object that determines which forms will open in a panel and at what size. Can be used to get and set.

            **New**, **Edit** and **Display** are all properties that specify each form's settings. 

            If not specified - specific form is automatically set to null, and not shown in a panel.
            
            |

            *Example:*
            
            .. code-block:: c#

                var fss = forms.GetFormSets();
                fss.Panel = new FormTypePanelSettings()
                {
                    Display = new FormPanelSettings()
                    {
                        Size = FormPanelSize.Medium
                    },
                    Edit = new FormPanelSettings()
                    {
                        Size = FormPanelSize.Large
                    },
                    New = null
                };

    *   -   **CustomListViewCode**
        -   Contains string with custom code for List View Commands. Can be used to get and set.
            
            |

            *Example:*
            
            .. code-block:: c#

                var fss = forms.GetFormSets();
                ffs.CustomListViewCode = "alert('Form Panels active')";