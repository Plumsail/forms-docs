Send an email on form submission
==================================================

Description
--------------------------------------------------

One of the basic functionalities you can add to your form is to send an email once the form is submitted. 
It can be used in variety of cases - to receive feedback from the clients, to get latest update from your employees and just to get some information in general.

In this example, we will design the form for customers to report their problems and use Flow to send submitted information to our company's `Helpdesk <https://plumsail.com/sharepoint-helpdesk/>`_.

Design a form
--------------------------------------------------

First, design the form. Think about what information you might need in the email, what can be used as a subject for the email, etc.

Here's the simple form designed to receive customers feedback on Forms Designer problems:

.. image:: ../images/how-to/email/1_DesignForm.png
   :alt: MultilineTextBox

|

Once you design and save the form, you will see General Settings button pop up on top. This section contains important information you'll need to use while setting up the Flow:

.. image:: ../images/how-to/email/6_GeneralSettings.png
   :alt: General Settings

|

**Important!** If you add changes the form, you first need to save it and only after saving the information in General Settings will update.

Configure the Flow
--------------------------------------------------

.. image:: ../images/how-to/email/2_MyFlows.png
   :alt: My Flows

|

.. image:: ../images/how-to/email/3_CreateFromBlank.png
   :alt: Create from blank

|

.. image:: ../images/how-to/email/4_Search.png
   :alt: Search

|

.. image:: ../images/how-to/email/5_AddPlumsailTrigger.png
   :alt: Add Plumsail trigger

|

.. image:: ../images/how-to/email/7_AddID.png
   :alt: Add ID from General Settings

|

.. image:: ../images/how-to/email/8_JSON.png
   :alt: Parse JSON

|

.. image:: ../images/how-to/email/9_ContentAndSchema.png
   :alt: Add Content and Schema from General Settings

|

.. image:: ../images/how-to/email/10_SendAnEmail.png
   :alt: Send an email

|

.. image:: ../images/how-to/email/11_SaveFlow.png
   :alt: Save Flow

|

Final Result
--------------------------------------------------

.. image:: ../images/how-to/email/12_FormPreview.png
   :alt: Form Preview

|

.. image:: ../images/how-to/email/13_Ticket.png
   :alt: Ticket
   
|