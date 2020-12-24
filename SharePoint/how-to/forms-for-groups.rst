.. title:: Personalize SharePoint forms for user groups

.. meta::
   :description: Provide unique forms for users based on their membership in Azure AD, Office365 or SharePoint groups

Personalize form based on user group in Azure Ad or Office365
======================================================================================

This article will show you how to create custom forms for users of different groups. Some ways are easier than others, but we want you to see all available options.

.. contents::
 :local:
 :depth: 1

Routing based on SharePoint groups
--------------------------------------------------
This is the easiest option to customize forms for a user group. All you need to do is to create a new :doc:`Form Set <../designer/form-sets>`, and select which groups will be redirected to it:

|pic0|

.. |pic0| image:: ../images/how-to/forms-for-groups/how-to-forms-for-groups-form-set.gif
   :alt: Forms for groups

Then the users of this group will automatically redirect to it, all the others will still see only the default form.

For a practical example of how to customize forms for a specific SharePoint group, check out :doc:`add personal form for creating and tracking tickets to any SP page <../examples/ticket-management>`.

Routing based on O365 groups
--------------------------------------------------

Show/hide sections based on O365 groups
--------------------------------------------------