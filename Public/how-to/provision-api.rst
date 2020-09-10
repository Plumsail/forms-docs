
.. title:: Create and provision public web forms programmatically

.. meta::
   :description: Create new forms from scratch by specifying details for each row and cell, or edit existing forms in Visual Studio with our NuGet package

Create and provision Plumsail public web forms programmatically
=================================================================

It is possible to create forms from scratch and then provision them programmatically using **Plumsail.Forms.Public** |NuGet package|. 

Forms can also be edited, as well as deleted using the same NuGet package.

.. important:: Functionality of this method is limited to web editor's functionality. Only web editor's forms can be edited. Forms created this way will also be editable only in web editor.

In order to use the package, your project must be compatible with |.NET Standard 2.1|

.. |.NET Standard 2.1| raw:: html

   <a href="https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md" target="_blank">.NET Standard 2.1</a>

Find an example of how it can be used in our article - :doc:`Create a contact web form in Visual Studio<./provision-example>`.

.. |NuGet package| raw:: html

   <a href="https://www.nuget.org/packages/Plumsail.Forms.Public" target="_blank">NuGet package</a>

.. contents::
 :local:
 :depth: 1

Client
-------------------------------------------------------------

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Constructor
        -   Description/Examples

    *   -   **FormsClient(string login, string password);**
        -   FormsClient allows you to connect to your account to start working with its forms.

            **login** - your Plumsail Account login

            **password** - your Plumsail Account password
            
            |

            *Example:*
            
            .. code-block:: c#

                var client = new FormsClient("login", "password");
    *   -   **FormsClient(HttpClient httpClient);**
        -   An alternative constructor of the FormsClient that uses HttpClient instead.

            **httpClient** - HttpClient that you can configure
            
            |

            *Example:*
            
            .. code-block:: c#

                using System.Net.Http;
                using System.Net.Http.Headers;
                
                var httpClient = new HttpClient();
                httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", "<token>");
                var client = new FormsClient(httpClient);

    *   -   **NewForm(string name)**
        -   A method of the FormsClient to create a new public web form with the specified name
            
            **name** - name of the form
            
            |

            *Example:*
            
            .. code-block:: c#

                var form = client.NewForm("Form name");

    *   -   **GetForm(string formId)**
        -   Async method to get a specific form from account

            **formId** - ID of the form
            
            |

            *Example:*
            
            .. code-block:: c#

                // get forms list
                var forms = await client.GetForms();
                var formId = forms.First().Id;
                // get form
                var form = await client.GetForm(formId);
    
    *   -   **DeleteForm(string formId)**
        -   Async method to delete a specific form from account

            **formId** - ID of the form
            
            |

            *Example:*
            
            .. code-block:: c#

                var forms = await client.GetForms();
                var form = forms.First();
                await client.DeleteForm(form.Id);

Form
-------------------------------------------------------------
Use **NewForm(string name)** or **GetForm(string formId)** to start working with a form

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Method/Property
        -   Description/Examples   
    *   -   **SavePosts**
        -   Get or set this boolean property that determines if form submissions will be saved to your Plumsail Account or not.

            |

            *Example:*
            
            .. code-block:: c#

                form.SavePosts = true;

    *   -   **NotifyOwner**
        -   Get or set this boolean property that determines if form submissions will be sent as messages to your email or not.

            |

            *Example:*
            
            .. code-block:: c#

                form.NotifyOwner = true;
    *   -   **Enabled**
        -   Get or set this boolean property that determines if form submissions will be sent to the server or not.

            |

            *Example:*
            
            .. code-block:: c#

                form.Enabled  = true;
    *   -   **Save()**
        -   Async method to save the form layout and settings.

            |

            *Example:*
            
            .. code-block:: c#

                try
                {
                    await form.Save();
                }
                catch(InvalidLoginException)
                {
                    // Set correct authorization header
                }
                catch(BadRequestException ex)
                {
                    // ex.Message
                }

Layout
-------------------------------------------------------------
Layout is the main content of the form. It's the property that holds PC/Tablet/Phone layout data, as well as JavaScript, CSS and even the theme data of each form.

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Method/Property
        -   Description/Examples
    *   -   **Css**
        -   Get or set CSS code for the form.
            
            |

            *Example:*
            
            .. code-block:: c#

                form.Layout.Css = ".fd-form h1 { color: red }";
    *   -   **JavaScript**
        -   Get or set JavaScript code for the form.
            
            |

            *Example:*
            
            .. code-block:: c#

                form.Layout.JavaScript = "fd.rendered(function(){ fd.field('Name').value = 'John Bull' });";
    *   -   **Theme**
        -   Get or set theme used for the form. Use one of predefined themes such as *Blue*, *Compact*, *Default*, *Explicit*, *Gray*, *Green*, *Orange*, *Plumsail*, *Purple*, *Red*, *Smooth*, or *Soft*.
            
            |

            *Example:*
            
            .. code-block:: c#

                form.Layout.Theme = new Theme(PredefinedThemes.Compact);

    *   -   **PC/Tablet/Phone**
        -   Get or set grid that will nest the rest of the form. At least one of these must be filled before the form is saved.
        
            When creating a grid, make sure that each row's width is less or equal to 12.
            
            |

            *Example:*
            
            .. code-block:: c#
                
                
                form.Layout.PC = new Grid(
                    new GridRow(
                        new GridCell(new Text("Text1")
                        {
                            // configure control
                            Content = "This is form, created with using Designer.Public",
                            Class = "text-control-class",
                            Style = "border: 1px solid red;"
                        }, width: 6)
                        { Offset = 2, Class = "grid-cell-class" }, // configure cell
                        new GridCell(new Submit("Submit1")
                        {
                            Width = 300
                        }, width: 4)
                    )
                );

Fields and Controls
-------------------------------------------------------------
These can be placed inside of cells, and configured using their own properties.

.. list-table::
    :header-rows: 1
    :widths: 10 30

    *   -   Constructor
        -   Description/Examples
    *   -   **new Field/Control(string name)**

            **{**
              **prop = property**
            **}**
            
        -   Create fields or controls by giving them name and setting their properties.

            **name** - name of the field/control
            
            |

            *Example:*
            
            .. code-block:: c#

                new GridRow(
                    new GridCell(new SingleLineTextField("Name")
                    { 
                        Title = "Name",
                        ControlHint = "David Bowie",
                        Orientation = Orientation.Vertical
                    }, width: 6),
                    new GridCell(new DateField("Date")
                    {
                        Title = "Date",
                        ControlHint = "Today's date",
                        Required = true,
                        Orientation = Orientation.Vertical
                    }, width: 6)
                ),
                new GridRow(
                    new GridCell(new Submit("SubmitButton")
                    {
                        Width = 300
                    }, width: 6)
                )