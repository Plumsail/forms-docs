Installation
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

Sign in to Plumsail Account
--------------------------------------------------

Plumsail Account
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Plumsail Forms product uses our new service called Plumsail Account. Using Plumsail Account you can manage your licenses - for both SharePoint and Plumsail Forms, 
and copy widgets of your forms to publish them to any page on the web, not limited to SharePoint sites.

Plumsail Account is a new service we've recently implemented, so even if you were our client for a long time, you still need to register to get an Account. 

Register
**************************************************
You can register by filling out |location_link|.

.. |location_link| raw:: html

   <a href="https://auth.plumsail.com/account/register?ReturnUrl=http://account.plumsail.com/" target="_blank">this small form here</a>

Sign in
**************************************************
You can log in by going to the |location_link2| and entering your login and password. Make sure you've registered first.

.. |location_link2| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank">following page</a>


Download designer and start designing forms
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
You can download Forms Designer from your Plumsail Account in Forms Section on the Intro tab. 

When you open the Designer, select Plumsail instead of SharePoint unless you are specifically designing a form for SharePoint list or library.

Saved Forms can be copied from Plumsail Account Forms Section in the Forms tab.

Plumsail Forms for SharePoint 
--------------------------------------------------

Bind your SharePoint tenant to your Account
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In order to bind your SharePoint tenant to Plumsail account, you need to have permissions of tenant administrator. 
This is only necessary for installation and we are not storing or using your credentials in any way, only to get permission for installation.

Once you sign in to Plumsail Account, you'll need to go to Forms section. 


.. image:: /images/SPlicense/PlumsailAccount.png
   :alt: Plumsail Account

|

Select Licenses tab and add your SharePoint domain to SharePoint Licenses:


.. image:: /images/SPlicense/AddLicense.png
   :alt: Forms Licenses

|

You'll need to complete authorization and give permissions to the app, here is where you need a tenant administrator account. 

We do not store your information, it's only necessary for the installation. 


.. image:: /images/SPlicense/LicenseAdded.png
   :alt: Domain Added

|

Once you've added SharePoint license to your domain, you will be able to use Plumsail Forms for your lists and document libraries after completing the next step.

Install app package to your tenant
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Last thing you need to do, to include Plumsail Forms on your SharePoint sites, 
is to install Form Web Part package to your app catalog. You can download the package from the Intro section of your Plumsail Account area. 

To do it properly, follow `instruction from Microsoft <https://support.office.com/en-us/article/Use-the-App-Catalog-to-make-custom-business-apps-available-for-your-SharePoint-Online-environment-0b6ab336-8b83-423f-a06b-bcc52861cba0>`_.


.. image:: /images/appcatalog/UploadForms.png
   :alt: App Catalog

|

Once the app is added and distributed to all the sites and SharePoint domain added to Licenses section in Plumsail account, you can use Designer to design modern forms for any list or library in your domain.

Download designer and start designing forms for SharePoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Once you've added your SharePoint license to your Plumsail Account and distributed app across your sites using app catalog, 
it is time to download Forms Designer and start using it. You can download Forms Designer from your Plumsail Account in Forms Section on the Intro tab.

Simply choose SharePoint in Forms Designer during sign in, enter your site and credentials, and start working on the forms.
Saved forms will automatically replace default forms on your site.