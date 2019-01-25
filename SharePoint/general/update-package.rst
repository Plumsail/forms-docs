Update the app package
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

About updates
--------------------------------------------------
Occasionally, we'll need to update app package for SharePoint, in order to expand product's functionality and fix any issues which may appear with SharePoint updates.

Some changes to the app package can be minor, requiring you only to update the package in App Catalog. The latest version of the package can always be found in your |Plumsail Account|.

.. |Plumsail Account| raw:: html

   <a href="https://account.plumsail.com/forms/intro" target="_blank">Plumsail Account</a>

Sometimes, the changes are major, and this will require some extra steps to update the app fully. We try to keep these updates to a minimum, only releasing them when absolutely necessary.

Update from v.1.0.4.0 or earlier
---------------------------------------------------
If you are using app package *v.1.0.4.0* or an earlier version, you might face issues with Form Panel or with List or Library control. Latest features of the app also won't be available.

|pic1|

.. |pic1| image:: /images/appcatalog/package.png
   :alt: App Catalog package


To update to package *v.1.0.5.0* or later, you will also need to re-save all the forms that you have in the latest version of Plumsail Forms designer app. This will update the scripts on the page of each particular form, and fix many issues which might've been present otherwise.

.. important:: If you update the app package, without re-saving the forms, forms that haven't been saved will become unavailable.

Update from v.1.0.5.0
---------------------------------------------------
If you are updating from *v.1.0.5.0* to *v.1.0.6.0* or later, you wouldn't need to re-save all the forms, but in order to get full functionality and fix any issues with the forms opening in IE, you will need to go to the site, or multiple sites, where you use Plumsail Forms, go to Site contents -> Site Pages/PlumsailForms and find and delete **redirect.aspx**.

|pic2|

.. |pic2| image:: /images/appcatalog/redirect-aspx.png
   :alt: redirect.aspx page

This file is responsible for routing to a particular forms, to update it, you will need to open ANY form and save it using the latest version of the app. This will create new **redirect.aspx** and the link to this particular form will be updated. You won't need to delete the file again, simply re-save the forms that you have issues with, and they should be fixed.

Now, older forms will continue functioning properly, but in order to fix any issues with URLs - re-save the forms that give the error.