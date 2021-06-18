.. title:: Plumsail Forms Provisioning Form sets for SharePoint 

.. meta::
   :description: Example of provisioning Form sets with panel settings to a SharePoint site - follow this example to provision forms with panel settings

Provisioning Form sets and Panel settings
===========================================

Form sets are important. They contain Form Panel and List View settings, plus routing configuration, including groups used for redirection.

This article will show you how to work with :ref:`designer-formsetsettings` when provisioning forms.

.. contents::
 :local:
 :depth: 1
 
Get Form Set Settings
--------------------------------------------------
Here's an example how you can retrieve existing Form Set Settings:

.. code-block:: c#

    var forms = new FormsDesigner.SharePoint.FormsManager(ctx, list.Id, contentType.Id.ToString());
    var fs = forms.GetFormSets();

.. important:: Only available after customization of Form sets, for example, adding new Form Set or customizing the Panel.

Create new Form Set Settings
--------------------------------------------------
Here's an example how you can create new Form Set Settings:

.. code-block:: c#

    var fs = new FormSetSettings(){
        CustomRouting = "//JS code for custom routing",
        CustomListViewStyle = "//CSS code to apply in List View"
    };


Set Form sets
--------------------------------------------------
Here's an example how you can create new Form sets:

.. code-block:: c#

    fs.FormSets = new FormSet[]{
        new FormsDesigner.Data.SharePoint.FormSet()
        {
            Id = new Guid(),
            Title = "FormSet1",
            ExcludedGroupIds = new int[] { 1, 2, 3},
            IncludedGroupIds = new int[] { 4, 5, 6 },
            Order = 1
        },
        new FormsDesigner.Data.SharePoint.FormSet()
        {
            Id = new Guid(),
            Title = "FormSet2",
            IncludedGroupIds = new int[] { 4, 5, 6 },
            Order = 2
        }
    };

Create Panel settings
--------------------------------------------------
Here's an example how you can create new Panel settings:

.. code-block:: c#

    fs.Panel = new FormTypePanelSettings(){
        New = new FormPanelSettings(FormPanelSize.Small),
        Edit = new FormPanelSettings(FormPanelSize.Medium),
        Display = new FormPanelSettings(FormPanelSize.Large)
    };

Setting Form Set settings
--------------------------------------------------
Here's an example how you can set Form Set settings after configuring them:

.. code-block:: c#

    var formsNewSite = new FormsDesigner.SharePoint.FormsManager(ctx, list.Id, contentType.Id.ToString())
    formsNewSite.SetFormSets(fs);