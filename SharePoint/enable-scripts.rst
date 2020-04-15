Enabling scripting capabilities in SharePoint Online
======================================================

.. contents:: Contents:
 :local:
 :depth: 1

Introduction
--------------------------------------------------
Plumsail Forms requires scripting capabilities to be enabled on a target site. By default, this feature is disabled and only tenant admins are able to turn it on.

The easiest option here is to |give permissions to our Azure Active Directory app|, which will automatically enable scripting capabilities on a site you're saving forms to.

.. |give permissions to our Azure Active Directory app| raw:: html

   <a href="https://account.plumsail.com/forms/licenses-page" target="_blank">give permissions to our Azure Active Directory app</a>

|pic1|

.. |pic1| image:: /images/scripts/AppPemissions.png
   :alt: Give permissions to AAD app

We do not store your credentials, nor do we access the actual data in your tenant. If you don't want to do this - use the following options.

With Powershell commands
--------------------------------------------------
Recommended option for manually enabling custom scripts. Install |SharePoint Online Management Shell|. 

.. |SharePoint Online Management Shell| raw:: html

   <a href="https://www.microsoft.com/en-us/download/details.aspx?id=35588" target="_blank">SharePoint Online Management Shell</a>

Run the following Powershell commands:

.. code-block:: javascript

    $userCredential = Get-Credential
    Connect-SPOService -Url https://<organization>-admin.sharepoint.com -Credential $userCredential
    Set-SPOsite <site URL> -DenyAddAndCustomizePages 0


**<organization>** - this is the name of your organization, used in SharePoint URL. 

.. Note:: For example, if your URL is **https://plumsail.sharepoint.com** - use **https://plumsail-admin.sharepoint.com**

**<site URL>** - this is the URL of the site collection where you want to enable custom scripts and publish forms to. Make sure not to use a subsite URL.

In SharePoint Admin center
--------------------------------------------------
This option is easy, but it is not recommended, as it can take up to **24 hours to enable custom scripts**. This method applies to all site collections on the tenant.

Go to Microsoft 365 admin center:

|pic2|

.. |pic2| image:: /images/scripts/AdminM365.png
   :alt: Microsoft 365 admin center

Open SharePoint Admin Center:

|pic3|

.. |pic3| image:: /images/scripts/AdminSharePoint.png
   :alt: Admin center for SharePoint

Switch to classic mode in Settings, if your Admin Center opens in Modern UI:

|pic4|

.. |pic4| image:: /images/scripts/ClassicAdminSharePointNew.png
   :alt: Classic Admin center for SharePoint

Select **Settings** in the left menu:

|pic5|

.. |pic5| image:: /images/scripts/SharePointOnlineSettings.png
   :alt: SharePoint Online Settings

Under Custom Script make sure that the following options are selected under **Custom Script**: 

*Allow users to run custom script on personal sites*

*Allow users to run custom script on self-service created sites*

|pic6|

.. |pic6| image:: /images/scripts/EnableScriptingCapabilities.png
   :alt: Enable Scripting Capabilities

.. Important:: Always wait 24 hours before trying to save forms with this method.