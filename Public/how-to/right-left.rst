.. title:: Adapt public web forms to right-to-left languages

.. meta::
   :description: Some languages require form to be read right to left, for example, Arabic or Farsi. One line of code is enough to support right-to-left languages

How to adapt public web forms to right-to-left languages e.g. Arabic or Hebrew
===============================================================================
 
Some languages require form to be read right to left, for example, Arabic or Farsi. That would mean that all titles should be moved to the right, repositioned on the form.

This functionality is actually fully supported in **Plumsail Forms**! 

All you need to do, actually, is to open JS code editor:

|pic1|

.. |pic1| image:: ../images/how-to/export-pdf/JSEditor.png
   :alt: JS Editor in Plumsail Forms

Insert the following code:

.. code-block:: javascript

    fd.rendered(function() {
        $('body').addClass('k-rtl');
    })

Then **save the form**:

|pic2|

.. |pic2| image:: ../images/how-to/right-left/save.png
   :alt: Form saved


You'll get the following result in the browser:

|pic3|

.. |pic3| image:: ../images/how-to/right-left/form.png
   :alt: Form in the browser