Version history
==================================================

v1.3.2
--------------------------------------------------
SharePoint Fields **ID**, **Created By**, **Created**, **Modified By**, **Modified** can be added to the form, just like any other fields.

Plain Text and Rich Text controls now support display of SharePoint Fields, for example: *Current item #[ID] has been created by [Author]*. Simply place field's [Internal Name] in square brackets.

Simplified URL generation for SharePoint Forms, now :ref:`using query string<link-specific>` for parameters, instead of the hash. Allows linking to specific Form Sets and fixes issues with linking forms in IE. Need to :doc:`update the app package </general/update-package>` for the URL generation to update.

Various bug fixes

v1.3.1
--------------------------------------------------
Added ability to open forms in :doc:`Dialog Mode </javascript/dialog>`

Reworked field controls

Added option to set Ink Sketch and DataTable controls to ReadOnly mode,
if their data is saved to SharePoint field

Optimized performance

v1.2.2
--------------------------------------------------
Descriptions now will display for all SharePoint fields

Fixed issues with IE11 support

Fixed minor styling issues

v1.2.1
--------------------------------------------------
Updated date and time picker for SharePoint forms

Toggle button for SharePoint Yes/No field

Added more responsiveness to Date and Numeric controls

Support of uploading large files with the List or Library control

Fixed an issue with attaching files with special characters in file names, e.g. ampersands, to SharePoint Forms

v1.2.0
--------------------------------------------------
Added ability to :doc:`customize toolbar and buttons</javascript/toolbar>`.

v1.1.9
--------------------------------------------------
:ref:`designer-wizard` container has been added.

Several bug fixes.

v1.1.8
--------------------------------------------------
:ref:`designer-likert` control has been added.

v1.1.7
--------------------------------------------------
Forms now support Native Office 365 authentication.

Tabs and Accordion Panels can now be dragged-and-dropped in the designer - inside the container to switch places, 
to another container of the same type or even outside on the form to create a new container.

v1.1.6
--------------------------------------------------
Ink Sketch and Data Table controls can now be saved to a hidden SharePoint field.

v1.1.5
--------------------------------------------------
:doc:`SharePoint Form Panel </designer/panel>` functionality added.

v1.1.4
--------------------------------------------------
Added Export to PDF button.

DataTable has received :ref:`a new property<designer-datatable>` - New Line(Top or Bottom).

Minor bug fixes.

v1.1.3
--------------------------------------------------
SharePoint :ref:`designer-lookup` field has received an upgrade.

v1.1.0
--------------------------------------------------
Added theme support for Public Web Forms.

v1.0.9
--------------------------------------------------
Added advanced :ref:`designer-customrouting` to Modern SharePoint Forms.

v1.0.7
--------------------------------------------------
Added automatic routing to SharePoint :doc:`Form Sets </designer/form-sets>` based on the user's groups.

Added :doc:`theme support </designer/themes>` for Modern SharePoint Forms.

v1.0.5
--------------------------------------------------
Added :ref:`designer-listorlibrary` control - allows editing items or documents in related SharePoint Lists or Document Libraries.

Fixed default width of titles for vertically-oriented fields.

Fixed activation of Site Pages feature.

Fixed .NET framework prerequisites check.

Other minor bug fixes.

v1.0.4
--------------------------------------------------
Added a drop-down column type to DataTable.

Improved JS-framework: added *'ready'* event to User and Content Type SharePoint fields, *'disabled'* property to Data Tables.

Minor bug fixes.

v1.0.3
--------------------------------------------------
:ref:`designer-datatable` is added.

Minor bugfixes.

v1.0.2
--------------------------------------------------
:ref:`designer-captcha` is added.

v1.0.1
--------------------------------------------------
Initial release.