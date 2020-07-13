.. title:: Processing Plumsail Forms in Power Automate

.. meta::
   :description: How to get info from forms' submissions and use them in flows

Processing submissions of online forms designed with Plumsail Forms in Power Automate (MS Flow)
====================================================================================================

.. contents:: Contents:
 :local:
 :depth: 1

Introduction
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

Go to My Flows and click *+ New* >> *Automated-from blank*:

|pic1|

.. |pic1| image:: /images/flow/flow-01.png
   :alt: My Flows

In the pop-up dialog, in *Choose your flow's trigge* field search for *Plumsail Forms* and add *Plumsail Forms - Form is submitted* trigger:

|pic3|

.. |pic3| image:: /images/flow/flow-02.png
   :alt: Plumsail Forms - Form is submitted trigger

If this is your first Flow, at this point you'll need to **Sign in to** |Plumsail Account| from Flow, so you can start using your forms inside the Flow.

.. |Plumsail Account| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank"><b>Plumsail Account</b></a>

.. important:: You can only bind Flows to the forms that are stored in your Plumsail Account!

|pic4|

.. |pic4| image:: /images/flow/11_AuthorizationNew.png
   :alt: Sign in to Plumsail Account

Select the form that you want to track:

|pic_fin|

.. |pic_fin| image:: /images/flow/flow-select-form.png
   :alt: Select form in flow

That's it, after this action you can do pretty much anything with submitted data - it's parsed and ready to be used.

Check out our How-to documentation on examples of using MS Power Automate. For example, for :doc:`sending an email with flow </how-to/email>`.