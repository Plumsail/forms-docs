Microsoft Flow
==================================================

About Microsoft Flow
-------------------------------------------------------------
|Flow| allows you to integrate various apps and services by creating 
automatic workflows between them to collect data, synchronize files, receive notifications and much more.

.. |Flow| raw:: html

   <a href="https://flow.microsoft.com/en-us/" target="_blank">Microsoft Flow</a>

Plumsail Forms can be utilized with Microsoft Flow in a variety of ways. 
All the data submitted with Plumsail Forms goes through Microsoft Flow and only you can decide what to do with it. 
You can email clients' requests from your site to your Helpdesk, you can create or update SharePoint items from outside SharePoint 
and practically anything else you can think of.

Additionally, SharePoint forms can also be handled by Microsoft Flow upon submission, allowing you more freedom than regular Workflows ever could.

**You need to have Plumsail License for Forms in order to utilize our custom MS Flow Connector with your forms.**

*That includes SharePoint forms, if you want to submit data to Flow using Plumsail Forms connector.*

Creating custom connector
-------------------------------------------------------------
First step in configuring Microsoft Flow is to create custom connector to handle Plumsail Forms. 

You can do it through Office365 or by going to |Flow| homepage.

When you open Office365, go to Microsoft Flow page:

.. image:: /images/flow/0_Flow.png
   :alt: Flow

|

When the page opens, click the cog in the upper right corner and select *Custom Connectors* from dropdown menu:

.. image:: /images/flow/1_CustomConnectors.png
   :alt: Custom Connectors

|

Now, you'll need to click *+ Create custom connector* and select *Import an OpenAPI from URL* in the dropdown menu:

.. image:: /images/flow/2_CreateCustomConnector.png
   :alt: Create custom connector

|

Give this custom connector name **Plumsail Forms** and copy this URL for the OpenAPI **https://forms.plumsail.com/swagger/v1/swagger.json**

It should look like this:

.. image:: /images/flow/3_CreateCustomConnectorWindow.png
   :alt: Input Name and URL

|

Next you can customize the look of the connector with the icon and background. 

You can download our icon |Icon| and we recommend to use it with white background **#ffffff**

Nothing else need to be changed on this page:

.. |Icon| raw:: html

   <a href="https://forms.plumsail.com/images/connector.png" target="_blank">here</a>

.. image:: /images/flow/4_AdjustIcon.png
   :alt: Adjust Icon

|

Next page you need to fill in several things.

Client ID: **3d8caf5f-2f67-4b4a-9a81-2ee61709220f**

Client Secret: **yMAbxuJGw2497Q3D9aXQKNjH5UghBSyH**

And finally Refresh URL: **https://auth.plumsail.com/connect/token**

Everything else leave as it is:

.. image:: /images/flow/5_OAuthFixed.png
   :alt: OAuth

|

Finally, click Create Connector on the next page:

.. image:: /images/flow/6_CreateConnector.png
   :alt: Last click

.. _creating-flow:

Creating Flow
-------------------------------------------------------------

Now custom connector has been added and you can start creating Flows with it.

Go to My Flows and click *Create from blank*:

.. image:: /images/flow/8_MyFlows.png
   :alt: My Flows

|

On the next page, click *Search hundreds of connectors and triggers*:

.. image:: /images/flow/9_Search.png
   :alt: Search

|

Search for *Plumsail* and add *Plumsail Forms - Form is submitted* trigger:

.. image:: /images/flow/10_FormSubmittedTrigger.png
   :alt: Plumsail Forms - Form is submitted trigger

|

If this is your first Flow, at this point you'll need to **Sign in to** |Plumsail Account| from Flow, so you can start using your forms inside the Flow.

.. |Plumsail Account| raw:: html

   <a href="https://auth.plumsail.com/account/login" target="_blank"><b>Plumsail Account</b></a>

**Important!** You can only bind Flows to the forms that are stored in your Plumsail Account!

.. image:: /images/flow/11_Authorization.png
   :alt: Sign in to Plumsail Account

|

Now, you'll need to add the ID of the Form you want to track. You can enter ID of the form you already created or create and save a new form in the designer.

Form ID can be found and copied in **General Settings** in the Designer.

.. image:: /images/flow/11_FormID.png
   :alt: Form ID

|

After adding the trigger, search for *JSON* and add *Data Operations - Parse JSON* action to actually parse data received from the submitted form:

.. image:: /images/flow/12_ParseJSON.png
   :alt: Parse JSON

|

Here you will need to open the designer and the form that you want to track with the Flow. Save it and after saving, 
open **General Settings** and copy the *Form Schema*:

.. image:: /images/flow/13_FormSchema.png
   :alt: Form Schema

|

In *Parse JSON* action click *Content* and select **Body** in menu on the right. Insert copied *Form Schema* into *Schema* field:

.. image:: /images/flow/14_ParseJSONContent.png
   :alt: Form Schema

|

That's it, after this action you can do pretty much anything with submitted data.

Check out our How-to documentation on examples of using Flow. For example, for :doc:`sending an email </how-to/email>`.