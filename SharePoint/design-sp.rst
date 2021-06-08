.. title:: How to design modern forms for SharePoint Online in Office 365 and for SharePoint 2019

.. meta::
   :description: Learn all you need: how to launch the editor app, how to customize a form, how to create form sets, and more

Designing modern forms for SharePoint Online in Office 365 and SharePoint 2019
===============================================================================================================

.. contents::
 :local:
 :depth: 1

Connecting to a SharePoint List
**************************************************

SharePoint Online
---------------------------------------------------
After following all the steps of :doc:`SharePoint installation instruction (Office 365) </installation-sp>`, download and run |the designer application|.
Simply enter the URL of the site that you want to modify forms for:

|pic1|

.. |pic1| image:: /images/startSP/startSP-sign-in.png
   :alt: Sign In SharePoint Online

.. |the designer application| raw:: html

   <a href="https://account.plumsail.com/forms/intro" target="_blank">the designer application</a>

You'll then need to go through standard SharePoint authentication, make sure to use login with **Full Control permissions** on the site.

.. note::   If you want to logout from the previously selected user, just connect to the site once again and press Sign Out button:

            |sign-out|

            .. |sign-out| image:: /images/startSP/startSP-sign-out.png
               :alt: Sign out button


SharePoint On-Premises
---------------------------------------------------
After following all the steps of :doc:`SharePoint installation instruction (SharePoint 2019) </installation-2019>`, you can launch the designer app from desktop or use **Design Forms** button in the ribbon (make sure to activate Site Collection feature first):

|ribbonButton|

.. |ribbonButton| image:: /images/startSP/runFormsFromRibbon.png
   :alt: Run Forms from Ribbon

Enter the exact URL of the site that you want to customize list for. Unless your Windows desktop login is the same as your SharePoint login, you'll need to
remove the mark from **Login as current user** and use your SharePoint credentials instead:

|login2019|

.. |login2019| image:: /images/startSP/loginNotCurrent.png
   :alt: Sign In not as Windows user

Depending on the type of authentication you have on your site, you might need to try different types:

|authentication|

.. |authentication| image:: /images/startSP/authentication.png
   :alt: Select authentication

Working with New, Edit and Display forms
**************************************************
Once you connect to a SharePoint List, you can select which form you want to edit in the upper right corner of the editor:

|pic2|

.. |pic2| image:: /images/startSP/currentForm.png
   :alt: Select Form - New, Edit and Display

- **New Form** - only available for SharePoint Lists, not available in SharePoint Libraries. Form that you see when you click *+New Item*.
- **Edit Form** - form that allows you to edit values stored in an item, or properties of an uploaded file in SharePoint Library.
- **Display Form** - form that only allows you to see what values are stored in an item or check properties of an uploaded file, cannot edit.

Content Type
-------------------------------------------------

You can select which Content Type you want to customize forms for - each Content Type has its own forms:

|content-type|

.. |content-type| image:: /images/startSP/startSP-ContentType.png
   :alt: Select Content Type

Learning the basics of the editor's layout
**************************************************
In the designer, on the left, you have Containers, Controls and Fields that you can use on the form:

|pic3|

.. |pic3| image:: /images/startSP/elements.png
   :alt: Containers, Controls and Fields

Adding them to the form is easy, just drag and drop the desired elements to the form. You can change individualy configuration of each :doc:`Field </designer/fields-sp>`, 
:doc:`Control </designer/controls>` and :doc:`Container </designer/containers>` by selecting it with a click and then adjusting its properties in menu on the right:

|pic4|

.. |pic4| image:: /images/startSP/startSP-designer-properties.gif
   :alt: Field's Properties

By default, each element is placed inside a :ref:`designer-grid`. By adjusting PARENT GRID properties of each element, 
you adjust element's layout in regards to all other elements. You can learn more on :doc:`how to work with form layout </how-to/grid-advantages>`.

.. |Bootstrap Grid| raw:: html

   <a href="https://getbootstrap.com/docs/4.0/layout/grid/" target="_blank">Bootstrap Grid</a>

.. note::   We do not recommend adding Common Fields to SharePoint forms unless you know what exactly you want to do with them. By default, only SharePoint Fields
            store data when Item is saved, Common Fields lose all the data. If you want, you can use Common fields to perform some calculations on the form or 
            submit certain data to MS Flow using :doc:`Plumsail Forms </how-to/flow>` connector.

Mobile Layouts
-------------------------------------------------
You can customize :ref:`layout for mobile devices <designer-layouts>` by selecting device type in the Ribbon. Clicking red **X** under the layout will delete it:

|mobile|

.. |mobile| image:: /images/startSP/startSP-layouts.png
   :alt: Layouts icons

To find more about various buttons and options available in the editor, check out :doc:`our Ribbon actions article </designer/ribbon-actions>`.

Saving a form or multiple forms
**************************************************
Saving a form is easy - just click the Save button. Once the button is pressed, it gets grayed out and you'll see a message that says that the form is saving.
Please, **wait until the process is complete**. Meanwhile, you can continue working in the designer, but if you want to see the results in SharePoint, 
you need to wait until you see *Layout has been successfully saved* message:

|pic5|

.. |pic5| image:: /images/startSP/startSP-saving.gif
   :alt: Saving a form

You are also able to save multiple forms at once if you want them to share functionality. For example, if the form has no custom logic, 
it's often easier to save New, Edit and Display form at the same time. Just click the arrow symbol on the Save button and select which forms you want to
replace with the current one:

|pic7|

.. |pic7| image:: /images/startSP/startSP-saving-all.png
   :alt: Save multiple forms
   
Be careful when saving more than one form, it's easy to forget that two forms might have different JavaScript attached to them and overwrite existing code.

Resetting a form back to default or to previous version
********************************************************
If you decide that you no longer want to utilize a specific form, you can open it in the editor and click the Reset button:

|reset|

.. |reset| image:: /images/startSP/startSP-reset.png
   :alt: Reset the form

If you ever want to go back and revert some changes, you can always :doc:`restore a previous version of a form </how-to/form-versions>`.

Working with CSS and JavaScript
**************************************************
If you want to change the appearance of elements on the form, you can either edit Style property of the elements or apply custom styles with CSS editor.
Don't forget that you can give each element a class and then use it in CSS editor to apply styles by class.

|editors|

.. |editors| image:: /images/startSP/startSP-editors.png
   :alt: JavaScript and CSS editors

|

Another thing that you can alter on any form is JavaScript and with our rich :doc:`JavaScript API </javascript/general>` there is a lot that can be done with it.

Please, make sure that you are familiar with the events present in JavaScript API as these events need to be used in order to get access to all forms elements.
You can check out the practical examples of using JavaScript API to make forms more dynamic:

   .. toctree::
               :maxdepth: 1
               :titlesonly:

               Populate, hide, disable, make mandatory fields <how-to/conditional-fields>
               Manipulate Tabs, Accordions, and Wizards with JavaScript <how-to/conditional-containers> 
               Date and Time: calculate difference, adjust values <how-to/manipulate-date-field>
               Data Table: populate cells, calculate totals, duplicate rows <how-to/data-table-cases>
               Handle List or Library fields in inline editing mode <how-to/list-or-library-inline>

Providing unique Form Sets for different users
**************************************************
You are not limited to three Forms per Content Type. In fact, you can create many :doc:`Form Sets </designer/form-sets>` as necessary.
Add a new one by clicking the **+ sign**:

|pic9|

.. |pic9| image:: /images/startSP/addFormSet.png
   :alt: Add a Form Set

Common use for Form Sets is to provide unique :ref:`forms for members of certain groups <designer-grouprouting>`, easily configured in the menu when you create a new Form Set:

|pic10|

.. |pic10| image:: /images/startSP/azureADGroups.png
   :alt: Form Sets Group Configuration

But you are not limited to it. In fact, you can leave it empty and instead use :ref:`designer-customrouting` to redirect users to the appropriate form based on other conditions,
such as field values on the form or user's properties:

|pic11|

.. |pic11| image:: /images/startSP/startSP-designSP-routing.png
   :alt: Form Routing button

.. note::   This can also be used to provide :doc:`different forms for different languages </how-to/language>`.

Displaying Related Items/Documents on the form
**************************************************
:ref:`designer-listorlibrary` control allows you to show another SharePoint List or Library within the form. 
It also allows users to add new items, change or delete existing ones, directly from the current form.

|pic12|

.. |pic12| image:: /images/how-to/child-parent-form/result.png
   :alt: Parent Form with Children

What is even more impressive - it allows to :doc:`create Parent/Child relationship </how-to/child-parent-form>` between items in one list and items in another list very easily, 
without any code required. This connection can be established even across sites, using our :doc:`Lookup control </how-to/csl>`.

You also need to be aware that List or Library supports various means of filtering. For example, you can :doc:`set Root Folder property </how-to/root-folder>` 
either manually or with a script, and it will ensure that users can only see contents of this root folder and cannot see items higher in the hierarchy. 
:doc:`CAML filtering </how-to/caml-filter>` is also supported and can also be used to filter shown items by their field values, and it can be done dynamically as well.

.. note::   You can also :doc:`update properties of uploaded files </how-to/document-meta>` dynamically.

Configuring Lookup - cascading, filtering, and cross-site connection
**********************************************************************
You can also do a lot with the Lookup on the form. For example, you can use our custom **Lookup control** to setup :doc:`cross-site connection </how-to/csl>`:

|lookup-control|

.. |lookup-control| image:: /images/startSP/startSP-designSP-LookupControl.png
   :alt: Lookup control

Either Lookup control or a regular SharePoint field can then be further customized. For example, you can add :doc:`filtering and cascading functionality </how-to/lookup-filter>`:

|lookup-filter|

.. |lookup-filter| image:: /images/how-to/lookup-filter/how-to-lookup-filter-depends-on-person.png
   :alt: Lookup filter

Also, both can be customized, and you can :doc:`adjust display values </how-to/lookup-view>` in dropdown for your exact needs:

|lookup-view|

.. |lookup-view| image:: /images/how-to/lookup-view/example.png
   :alt: Lookup view customized