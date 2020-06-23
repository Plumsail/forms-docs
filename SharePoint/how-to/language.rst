How to create different SharePoint forms for alternative languages
===================================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Introduction
--------------------------------------------------
Modern SharePoint sites support large amount of languages. In your company, you might have users with different language preferences, all working on the same site.

|pic1|

.. |pic1| image:: ../images/how-to/language/languages.png
   :alt: Language settings

Plumsail Forms can support multiple languages for each form with a little bit of work.

.. important:: Previously, the implementation of different language forms worked differently. To get the latest functionality, please, :doc:`update the app package <../general/update-package>` to v1.0.8 or higher, and re-save forms in the editor v1.6.4 or higher.

Implementation
--------------------------------------------------
First, you'll need to create a :doc:`Form Set <../designer/form-sets>` for the language that you want to support:

|pic2|

.. |pic2| image:: ../images/how-to/language/how-to-language-add-form-set.png
   :alt: Add form set

This language will have to be available for the site:

|pic3|

.. |pic3| image:: ../images/how-to/language/how-to-language-available-languages.png
   :alt: Available languages

Then, you need to configure Custom Routing to redirect to this Form Set when the UI of the site is rendered with this language:

|pic4|

.. |pic4| image:: ../images/how-to/language/how-to-language-custom-routing.png
   :alt: Custom routing

Use code like this:

.. code-block:: javascript

    if(_spPageContextInfo.currentUICultureName == "es-ES"){
      return "b442f350-2949-4d95-b13c-ac4063ab34e4";
   }

You only need to replace **"es-ES"** with the name of the |language/culture| you want supported and the ID of the Form Set can be copied at the bottom of the editor:

|pic5|

.. |pic5| image:: ../images/how-to/language/how-to-language-form-set-id.png
   :alt: Form Set ID

.. |language/culture| raw:: html

   <a href="https://docs.microsoft.com/en-us/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes" target="_blank">language/culture</a>

