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

You can download our icon :download:`here </images/icons/FormsIcon.png>` and we recommend to use it with white background **#ffffff**

Nothing else need to be changed on this page:

.. image:: /images/flow/4_AdjustIcon.png
   :alt: Adjust Icon

|

Next page you need to fill in several things.

Client ID: **3d8caf5f-2f67-4b4a-9a81-2ee61709220f**

Client Secret: **yMAbxuJGw2497Q3D9aXQKNjH5UghBSyH**

And finally Refresh URL: **https://auth.plumsail.com/connect/revocation**

Everything else leave as it is:

.. image:: /images/flow/5_OAuth.png
   :alt: OAuth

|

Finally, click Create Connector on the next page:

.. image:: /images/flow/6_CreateConnector.png
   :alt: Last click

Authorization
-------------------------------------------------------------

Now custom connector has been added, but you need to complete authorization to make it work.

Go back to Custom Connectors page where you now have Plumsail Forms and click big **+** sign right to it.

It will open Authentication pop up where you need to Sign in to your Plumsail account. It must be the same account where you store all your forms.

.. image:: /images/flow/7_CreateConnection.png
   :alt: Create connection

|

Now you can create custom flows and utilize Plumsail Forms to their full advantage.