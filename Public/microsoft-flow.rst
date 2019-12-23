Handling data in Power Automate (MS Flow)
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

About Power Automate
-------------------------------------------------------------
|Flow| allows you to integrate various apps and services by creating 
automatic workflows between them to collect data, synchronize files, receive notifications and much more.

.. |Flow| raw:: html

   <a href="https://flow.microsoft.com/en-us/" target="_blank">Power Automate (MS Flow)</a>

Plumsail Forms can be utilized with Power Automate in a variety of ways. 
Data submitted with Plumsail Forms can go through flows and only you decide what to do with it:
you can email clients' requests from your site to your Helpdesk, you can create or update SharePoint items from outside SharePoint 
or do practically anything else you can think of.

Additionally, SharePoint forms can also be handled by flows upon submission, allowing you more freedom than regular Workflows ever could.

.. note:: The amount of data that can be handled by Plumsail Forms connector depends on your current plan of Plumsail Forms subscription.

.. _creating-flow:

Creating flow
-------------------------------------------------------------

Go to My Flows and click *Create from blank*:

|pic1|

.. |pic1| image:: /images/flow/8_MyFlows.png
   :alt: My Flows

On the next page, click *Search hundreds of connectors and triggers*:

|pic2|

.. |pic2| image:: /images/flow/9_Search.png
   :alt: Search

Search for *Plumsail Forms* and add *Plumsail Forms - Form is submitted* trigger:

|pic3|

.. |pic3| image:: /images/flow/10_FormSubmittedTriggerNew.png
   :alt: Plumsail Forms - Form is submitted trigger

If this is your first Flow, at this point you'll need to **Sign in to** |Plumsail Account| from Flow, so you can start using your forms inside the Flow.

.. |Plumsail Account| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank"><b>Plumsail Account</b></a>

.. important:: You can only bind Flows to the forms that are stored in your Plumsail Account!

|pic4|

.. |pic4| image:: /images/flow/11_AuthorizationNew.png
   :alt: Sign in to Plumsail Account

Now, you'll need to add the ID of the Form you want to track. You can enter ID of the form you already created or create and save a new form in the designer.

Form ID can be found and copied in **General Settings** in the Designer.

|pic5|

.. |pic5| image:: /images/flow/11_FormIDNew.png
   :alt: Form ID

That's it, after this action you can do pretty much anything with submitted data - it's parsed and ready to be used.

Check out our How-to documentation on examples of using MS Power Automate. For example, for :doc:`sending an email with flow </how-to/email>`.