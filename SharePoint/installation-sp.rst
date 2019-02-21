SharePoint Online Installation (Office365)
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

First step - Register a Plumsail Account
--------------------------------------------------
Plumsail Forms product uses our service called Plumsail Account. Using Plumsail Account you can manage your licenses - for both Modern SharePoint and Public Web Forms, 
and it also stores all your Public Web Forms. 

Register
**************************************************
You can register by filling out |location_link|.

.. |location_link| raw:: html

   <a href="https://auth.plumsail.com/account/register?ReturnUrl=http://account.plumsail.com/" target="_blank">Plumsail Account registration form</a>

Sign in
**************************************************
You can log in by going to the |location_link2| and entering your login and password. Make sure you've registered first.

.. |location_link2| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank">Plumsail Account login page</a>

Plumsail Forms for SharePoint Online
--------------------------------------------------

Bind your SharePoint tenant to your Account
**************************************************
In order to bind your SharePoint tenant to Plumsail account, you need to have permissions of **tenant administrator**. 

.. note:: This is only necessary for installation and we are not storing or using your credentials in any way, only to get permission for the installation.

Once you sign in to Plumsail Account, you'll need to go to Forms section. 

|pic1|

.. |pic1| image:: /images/SPlicense/PlumsailAccount.png
   :alt: Plumsail Account

Select Licenses tab and add your SharePoint domain to SharePoint Licenses.

You'll need to complete authorization and give permissions to the app, here is where you need a **tenant administrator** account. 

It's only necessary for this step:

|pic2|

.. |pic2| image:: /images/SPlicense/AddLicense.png
   :alt: Forms Licenses

Once you've added SharePoint license to your domain, you will be able to use Plumsail Forms for your lists and document libraries after completing the next step.

|pic3|

.. |pic3| image:: /images/SPlicense/LicenseAdded.png
   :alt: Domain Added

.. _install-app-package:

Install app package to your tenant
**************************************************
Last thing you need to do, to include Plumsail Forms on your SharePoint sites, 
is to install Form Web Part package to your App Catalog. You can download the package from the Intro section of your Plumsail Account area. 

|download-pack|

.. |download-pack| image:: /images/startSP/download.png
   :alt: Download package

To do it properly, follow `App Catalog instruction from Microsoft <https://support.office.com/en-us/article/Use-the-App-Catalog-to-make-custom-business-apps-available-for-your-SharePoint-Online-environment-0b6ab336-8b83-423f-a06b-bcc52861cba0>`_.

|pic4|

.. |pic4| image:: /images/appcatalog/UploadForms.png
   :alt: App Catalog

Once the app is added and distributed to all the sites and SharePoint domain added to Licenses section in Plumsail account, 
you can use Designer to design modern forms for any list or library in your domain.

There are no downsides to distributing the app to all sites - it simply gives you an ability to replace any form, 
but it won't replace any forms that you haven't edited and saved yourself. If you change your mind about a particular form,
you can always reset it to default as well.

Download designer and start designing forms for SharePoint
***********************************************************
Once you've added your SharePoint license to your Plumsail Account and distributed app across your sites using App Catalog, 
it is time to download Forms Designer and start using it. You can |download| from your Plumsail Account in Forms Section in the Intro tab.

|pic5|

.. |pic5| image:: /images/startSP/install.png
   :alt: Install Forms Designer

.. |download| raw:: html

   <a href="https://account.plumsail.com/forms/intro" target="_blank">download the designer app</a>

Find more about :doc:`how to design Modern SharePoint Forms with the designer </design-sp>`.