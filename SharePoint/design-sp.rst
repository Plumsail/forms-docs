Designing SharePoint forms
=====================================

.. contents:: Contents:
 :local:
 :depth: 1


Open the designer
**************************************************
First of all, you need to make sure that you've downloaded and installed |the designer application| to your PC.

Don't forget to follow all the steps in the :doc:`SharePoint installation instruction (Office365) </installation-sp>` 
or :doc:`SharePoint installation instruction (SharePoint 2019) </installation-2019>`, 
upload package to your App Catalog and share it with all the sites.

.. |Plumsail Account| raw:: html

   <a href="https://account.plumsail.com/" target="_blank">Plumsail Account</a>

.. |the designer application| raw:: html

   <a href="https://account.plumsail.com/forms/intro" target="_blank">the designer application</a>

SharePoint Online
---------------------------------------------------
For SharePoint Online app launches with the following window:

|pic1|

.. |pic1| image:: /images/startSP/signIn.png
   :alt: Sign In SharePoint Online

Simply choose SharePoint in Forms Designer during sign in, enter your site's URL and Site Owner credentials, select a List or a Library 
forms for which you want to modify and start working on the forms. Saved forms will automatically replace default forms on your site.

SharePoint On-Premises
---------------------------------------------------
You can launch the designer app from desktop or use **Design Forms** button in the ribbon (make sure to activate Site Collection feature first):

|ribbonButton|

.. |ribbonButton| image:: /images/startSP/runFormsFromRibbon.png
   :alt: Run Forms from Ribbon

For SharePoint On-Premises app launches with the following window:

|designer2019|

.. |designer2019| image:: /images/startSP/launch2019.png
   :alt: Sign In SharePoint 2019

Enter the exact URL of the site that you want to customize list for. Unless your Windows desktop login is the same as your SharePoint login, you'll need to
remove the mark from **Login as current user** and use your SharePoint credentials instead:

|login2019|

.. |login2019| image:: /images/startSP/loginNotCurrent.png
   :alt: Sign In not as Windows user

Depending on the type of authentication you have on your site, you might need to try different types:

|authentication|

.. |authentication| image:: /images/startSP/authentication.png
   :alt: Select authentication

New, Edit and Display forms
**************************************************
Inside the designer, when you open a specific List or a Library to work with, you can select which form you want to edit in the upper right corner.

|pic2|

.. |pic2| image:: /images/startSP/currentForm.png
   :alt: Select Form - New, Edit and Display

- **New Form** - only available for SharePoint Lists, not available in SharePoint Libraries. Form that you see when you click *+New Item*.
- **Edit Form** - form that allows you to edit values stored in an item, or properties of an uploaded file in SharePoint Library.
- **Display Form** - form that only allows you to see what values are stored in an item or check properties of an uploaded file, cannot edit.

Content Type
-------------------------------------------------

Also, if Content Types are enabled for the List, you can select which Content Type you want to customize forms for:

|content-type|

.. |content-type| image:: /images/startSP/contentType.png
   :alt: Select Content Type

Each Content Type has its own forms.

Basics of form design
**************************************************
In the designer, on the left, you have Containers, Controls and Fields that you can use on the form:

|pic3|

.. |pic3| image:: /images/startSP/elements.png
   :alt: Containers, Controls and Fields

Adding them to the form is easy, just drag and drop the desired elements to the form. You can change individualy configuration of each :doc:`Field </designer/fields>`, 
:doc:`Control </designer/controls>` and :doc:`Container </designer/containers>` by selecting it with a click and then adjusting its properties in menu on the right:

|pic4|

.. |pic4| image:: /images/startSP/settings.png
   :alt: Field's Properties

By default, each element is placed inside a :ref:`designer-grid`, which is based on |Bootstrap Grid|. By adjusting PARENT GRID properties of each element, 
you adjust element's layout in regards to all other elements.

.. |Bootstrap Grid| raw:: html

   <a href="https://getbootstrap.com/docs/4.0/layout/grid/" target="_blank">Bootstrap Grid</a>

.. note::   We do not recommend adding Common Fields to SharePoint forms unless you know what exactly you want to do with them. By default, only SharePoint Fields
            store data when Item is saved, Common Fields lose all the data. If you want, you can use Common fields to perform some calculations on the form or 
            submit certain data to MS Flow using :doc:`Plumsail Forms </how-to/flow>` connector.

Mobile Layouts
-------------------------------------------------
You can customize :ref:`layout for mobile devices <designer-layouts>` by selecting device type in the Ribbon. Clicking red **X** under the layout will delete it:

|mobile|

.. |mobile| image:: /images/designer/ribbon-actions/Layouts.png
   :alt: Layouts icons

Saving a form
**************************************************
Saving a form is easy - just click the Save button. Once the button is pressed, it gets grayed out and you'll see a message that says that the form is saving:

|pic5|

.. |pic5| image:: /images/startSP/saving.png
   :alt: Saving a form
   :width: 80%

|

Please, **wait until the process is complete**. Meanwhile, you can continue working in the designer, but if you want to see the results in SharePoint, 
you need to wait until you see *Layout has been successfully saved* message:

|pic6|

.. |pic6| image:: /images/startSP/saved.png
   :alt: Form is saved
   :width: 80%

|

Finally, you are also able to save multiple forms at once if you want them to share functionality. For example, if the form has no custom logic, 
it's often easier to save New, Edit and Display form at the same time. Just click the arrow symbol on the Save button and select which forms you want to
replace with the current one:

|pic7|

.. |pic7| image:: /images/startSP/save3.png
   :alt: Save multiple forms

|

Be extra careful when saving more than one form, it's easy to forget that two forms might have different JavaScript attached to them, for example.
Because of that, and other potentially risky situations, we recommend backing up forms that are important to you, 
by using :ref:`Export feature <designer-export>` of the designer:

|pic8|

.. |pic8| image:: /images/designer/ribbon-actions/ExportImport.png
   :alt: Export and Import buttons

Advanced functionality
**************************************************

CSS and JavaScript
--------------------------------------------------
If you want to change the appearance of elements on the form, you can either edit Style property of the elements or apply custom styles with CSS editor.
Don't forget that you can give each element a class and then use it in CSS editor to apply styles by class.

|editors|

.. |editors| image:: /images/startSP/editors.png
   :alt: JavaScript and CSS editors

|

Another thing that you can alter on any form is JavaScript and with our rich :doc:`JavaScript API </javascript/general>` there is a lot that can be done with it.

Please, make sure that you are familiar with the events present in JavaScript API as these events need to be used in order to get access to all forms elements.
In this section you can check out the practical examples of using JavaScript API to make forms more dynamic.

Form Sets
--------------------------------------------------
You are not limited to three Forms per Content Type. In fact, you can create many :doc:`Form Sets </designer/form-sets>` as necessary.
Add a new one by clicking the **+ sign**:

|pic9|

.. |pic9| image:: /images/startSP/addFormSet.png
   :alt: Add a Form Set

Common use for Form Sets is to provide unique :ref:`forms for members of certain groups <designer-grouprouting>`, that can be easily configured in the menu when you create a new Form Set:

|pic10|

.. |pic10| image:: /images/designer/form-sets/2-FormSetsConfig.png
   :alt: Form Sets Group Configuration

But you are not limited to it. In fact, you can leave it empty and instead use :ref:`designer-customrouting` to redirect users to the appropriate form based on other conditions,
such as field values on the form or user's properties:

|pic11|

.. |pic11| image:: /images/designer/form-sets/3-Routing.png
   :alt: Form Routing button

Related Items/Documents
--------------------------------------------------
:ref:`designer-listorlibrary` control allows you to show another SharePoint List or Library within the form. 
It also allows users to add new items, change or delete existing ones, directly from the current form.

|pic12|

.. |pic12| image:: /images/how-to/child-parent-form/result.png
   :alt: Parent Form with Children

What is even more impressive - it allows to :doc:`create Parent/Child relationship </how-to/child-parent-form>` between items in one list and items in another list very easily, 
without any code required. Find out how it's done in this article.

You also need to be aware that List or Library supports various means of filtering. For example, you can :doc:`set Root Folder property </how-to/root-folder>` 
either manually or with a script, and it will ensure that users can only see contents of this root folder and cannot see items higher in the hierarchy. 
:doc:`CAML filtering </how-to/caml-filter>` is also supported and can also be used to filter shown items by their field values, and it can be done dynamically as well.