Ribbon Actions
==================================================

Layouts - PC, Tablet or Phone
--------------------------------------------------
Modern Plumsail Forms are built to be responsive. On top of utilizing |Bootstrap| for its elements, Forms can also be specifically designed for different devices.

.. |Bootstrap| raw:: html

   <a href="https://getbootstrap.com/" target="_blank">Bootstrap 4</a>

Plumsail Forms do not simply rely on the screen size, instead the appropriate Form is chosen based on browser's user agent and then displayed. 
Phone forms are displayed for smartphones, Tablet forms are displayed for tablets and other devices utilize PC Form which is the default one.

Designing Forms
**************************************************
Designing forms for different devices has never been easier. All you need to do, is click 
the icon of the device you want to design form for, customize the form and click Save.

The red cross under the icon of the device indicates that the form is registered. Click on it to remove the specific form. 
There will be a confirmation prompt to avoid potential misclicks: 

.. image:: /images/designer/ribbon-actions/Layouts.png
   :alt: Layouts icons

|

**Important!** Make sure that the fields present on different layouts have the same internal names 
and the same type to avoid errors on submission in Microsoft Flow. These can be different fields with the same name as long as the type is the same, for example, 
Textbox and MultilineTextBox.

Testing Forms
**************************************************
For testing purposes, you can just change user agent in your browser to see a different form. For example, when using Google Chrome you can open Developers tools
and click Toggle device toolbar icon next to Inspector which will allow you to change the device and see how the form is displayed on other devices.

.. image:: /images/designer/ribbon-actions/ToggleDeviceToolbar.png
   :alt: Toggle Device Toolbar

|
Similar functionality is present in almost all modern browsers.

Export and Import
--------------------------------------------------
You can export currently selected form by pressing Export button. It will allow you to save the form as a file on your computer.

.. image:: /images/designer/ribbon-actions/ExportImport.png
   :alt: Export and Import
|

This can be used in variety of situations, especially if you need to design a number of similar forms. 

We also recommend storing backups for your important and/or complex forms, 
so if somebody changes the form later, it would be possible to restore it quickly.

Finally, you can import forms from the exported files, either yours or somebody else's, by pressing the Import button and selecting the form to import.

General Settings and Preview
--------------------------------------------------
These two buttons appear on the ribbon only after you've saved the form. They also differ for Plumsail forms and SharePoint forms, as SharePoint forms get different General Settings and no Form Preview.

.. image:: /images/designer/ribbon-actions/GenSettingsPreview.png
   :alt: General Settings and Preview

|

**General Settings for Plumsail forms** section contains important information for Flow configuration, including Form ID and Form Schema,
as well as the widget that you can copy to insert form to a webpage for Plumsail Forms.

You can select if you want to submit form to Flow which needs to be checked if you want to use the form with Microsoft Flow and it is turned on by default.
You still need to configure the Flow to actually do something with the submitted data.

Be careful with Form Schema when updating the form, it only changes after the form has been saved.

.. image:: /images/designer/ribbon-actions/GeneralSettings.png
   :alt: General Settings for Plumsail forms

|

**General Settings for SharePoint forms** contain no widget as the form can only be opened from the SharePoint list or library.

Here, you can also select if you want to submit form to Flow which needs to be checked if you want to use the form with Microsoft Flow, 
but it is turned off by default.
You still need to configure the Flow to actually do something with the submitted data.

You can also generate, edit or copy Form ID for SharePoint forms. 
This allows you to give the same ID to multiple forms, so that Flow handles submission from more than one form.
You still need to make sure that fields have the same internal names.

This can be useful if you want to handle submission of both New and Edit Form through Microsoft Flow, so you don't have to create different Flows for it.
But make sure that Form IDs are different for your forms if you only want to handle one form with specific Flow.

Finally, Form Schema is also available for SharePoint forms and it also updates on Save, so don't forget to Save prior to copying it.

.. image:: /images/designer/ribbon-actions/GeneralSettingsSP.png
   :alt: General Settings for SharePoint forms

|

**Preview** button allows you to quickly open Plumsail Forms in your default browser:

.. image:: /images/designer/ribbon-actions/FormPreview.png
   :alt: Form Preview

|