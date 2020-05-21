SharePoint web part for publishing a SharePoint form to any modern page within the tenant (Office 365) or web application (SharePoint 2019)
====================================================================================================================================================================

.. contents:: Contents:
 :local:
 :depth: 1

Plumsail Forms Web Part
-------------------------------------------------------------
New Web Part will allow you to publish any Public or SharePoint Form to any page. 

.. important:: You need to :doc:`update the app package </general/update-package>` to version 1.0.7.0

You can add Web Part to any Modern page:

|pic1|

.. |pic1| image:: ../images/designer/web-part/WebPart.png
   :alt: Add Web Part

SharePoint Form
-------------------------------------------------------------
If you want to publish SharePoint Form, select Site URL, List and Content Type in Web part settings:

|pic3|

.. |pic3| image:: ../images/designer/web-part/ConfigureWebPart.png
   :alt: Configure SharePoint Form

Then, **as long as user has access** to the form's List, they'll see the form on the page:

|pic4|

.. |pic4| image:: ../images/designer/web-part/WebPartForm.png
   :alt: Published SharePoint Form

You can even have several forms published on the same page:

|pic5|

.. |pic5| image:: ../images/designer/web-part/WebPartDual.png
   :alt: Multiple Forms Published

You can also use Edit or Display Forms, by either providing a constant item ID:

|pic6|

.. |pic6| image:: ../images/designer/web-part/EditDisplayWebPartConst.png
   :alt: Edit or Display Form with constant ID

Or using a query parameter to specify the item:

|pic7|

.. |pic7| image:: ../images/designer/web-part/QueryParamWebPart.png
   :alt: Item based on query parameter

This query parameter will be taken from the page's URL which you can add before sharing a link with someone:

|pic8|

.. |pic8| image:: ../images/designer/web-part/QueryParamURLWebPart.png
   :alt: Query parameter in URL

To make sure the users get the correct form for them, please, use :doc:`Form Sets </designer/form-sets>`.

For more detail on using the form web part with form sets, :doc:`read the article </how-to/personal-form>`.

Public Web Form
-------------------------------------------------------------
If you want to publish Public Web Form, simply create it, save it, open General settings and copy Form ID to the Web Part:

|pic2|

.. |pic2| image:: ../images/designer/web-part/WebPartPublic.png
   :alt: Publish Public Web Form

The form will then be submitted to Flow, where you can `process it <https://plumsail.com/docs/forms-web/microsoft-flow.html>`_.

Examples
-----------------------------------------------------

Learn how to embed web form or SharePoint form into Microsoft Teams in :doc:`this</examples/ms-teams>` article. 