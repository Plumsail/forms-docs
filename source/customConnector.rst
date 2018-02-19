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