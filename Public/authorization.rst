:orphan:

.. title:: Authorization for public web forms

.. meta::
   :description: Set up access via Microsoft Account, restrict access to some SharePoint users or Azure AD groups

Authorization for public web forms
=====================================
After saving a form, go to Settings → Sharing where you can find Access management.

First setting available is a toggle **Allow only authenticated users (Microsoft Account)**:

|ms-account|

.. |ms-account| image:: /images/authorization/authorization-ms-account.png
   :alt: Allow only authenticated users (Microsoft Account)

Once you turn it on - users will need to be authorized. New settings will become available to choose from.

You can restrict submissions to just one per user. If you do - you can also allow users to go back to form and edit their submission (each edit counts as a submission and will trigger a flow/zap again):

|just-once|

.. |just-once| image:: /images/authorization/authorization-just-once.gif
   :alt: Allow users to submit the form just once

Finally, you can restrict access to specific users by enabling **Restrict access to specific users or groups (Azure AD)** and inputting a Microsoft 365 domain:

|domain|

.. |domain| image:: /images/authorization/authorization-domain.png
   :alt: Restrict access to a domain

This will require you to authorize the app to access domain and retrieve information about the users:

|permissions|

.. |permissions| image:: /images/authorization/authorization-permissions.png
   :alt: Grant permissions to the permissions

On top of that, you will also be able to select specific Azure Active Directory groups or even individual users to provide access to:

|groups|

.. |groups| image:: /images/authorization/authorization-groups-and-users.png
   :alt: Limit access to specific users/Azure AD groups

Users without permissions will not be able to access the form:

|no-permissions|

.. |no-permissions| image:: /images/authorization/authorization-no-permissions.png
   :alt: No access to the form