.. title:: Processing Plumsail Forms in Zapier

.. meta::
   :description: How to get info from forms' submissions with our connector and use them in your zaps

Processing submissions of online forms designed with Plumsail Forms in Zapier
==========================================================================================

.. contents:: Contents:
 :local:
 :depth: 1

Introduction
-------------------------------------------------------------
|Zapier| is a web-based service that allows you to integrate various web applications with
automatic workflows. It includes the majority of popular apps, such as Gmail, Google Documents, Buffer, Mail Chimp, SendinBlue, Instagram, Twitter and many more.

.. |Zapier| raw:: html

   <a href="https://zapier.com/" target="_blank">Zapier</a>

Plumsail Forms can be utilized with Zapier in a variety of ways. 
Just like with Power Automate (MS Flow), you can use our Plumsail Forms app to receive form submissions.
Then you can integrate it with the other available applications and do anything with the submitted data - send an email, upload files to Google Docs or Dropbox, even add attachment photos to Instagram, everything is possible.

.. note:: The amount of data that can be handled by Plumsail Forms app depends on your current plan of Plumsail Forms subscription.

.. _creating-zap:

Creating a Zap
-------------------------------------------------------------
Search for *Plumsail Forms* and add the latest version of the app:

|pic3|

.. |pic3| image:: /images/zapier/zapier-search-plumsail-forms.png
   :alt: Search for Plumsail Forms

Select *New Submission* of a form as a Trigger and click Continue:

|pic4|

.. |pic4| image:: /images/zapier/zapier-new-submission.png
   :alt: New Submission

If this is your first Zap, at this point you'll need to **Sign in to** |Plumsail Account| from Zapier, so the connection is established between the app and your account. If you already have an account tied to the app, you can add another one at this step, and use it instead.

.. |Plumsail Account| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank"><b>Plumsail Account</b></a>

.. important:: You can only bind Zaps to the forms that are stored in your Plumsail Account!

Now, you just need to select the form that you want to use in the dropdown menu, no copying ID or Form Schema is required, it's all done automatically, but loading all the forms can take time, please, remain patient and soon all the forms from your account would be loaded and you'll be able to select the correct one:

|pic5|

.. |pic5| image:: /images/zapier/select-form.png
   :alt: Select a Form

In the next step, you can just click *Pull in Samples* (this will let the app know what fields are present on the form):

|pic6|

.. |pic6| image:: /images/zapier/pull-in-samples.png
   :alt: Pull in Samples

Select *Sample A* and press Continue:

|pic7|

.. |pic7| image:: /images/zapier/sample-a.png
   :alt: Select Sample A

Now, you just need to choose any of the apps and use the data received from form inside of these applications:

|pic8|

.. |pic8| image:: /images/zapier/choose-action.png
   :alt: Choose an Action app

Once you choose an app, fill in its fields with the information from the form, like this:

|pic9|

.. |pic9| image:: /images/zapier/fill-in.png
   :alt: Fill-in fields

When you finish configuring a Zap you can give it a name and save it, so it's easier for you to find it later. Don't forget to turn on the Zap in the end:

|pic10|

.. |pic10| image:: /images/zapier/zap-is-on.png
   :alt: The Zap is working

Now, each time the form is submitted, it will also be sent to Zapier, parsed and then used as set up in your Zap.