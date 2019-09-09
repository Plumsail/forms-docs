Passing values from a parent form to a child opened in a dialog 
===============================================================================

.. contents:: Contents:
 :local:
 :depth: 1

Introduction 
--------------------------------------------------

In this article, you will find the instructions for passing the values from a parent form to a child form, which are opened in a dialog.

|pic0|

.. |pic0| image:: ../images/how-to/pass-values/pass-values-0.gif
   :alt: preview

Suppose that you're developing a facility management system where a company possesses a set off the facilities. And in case of any issue at a facility, a user creates an issue which is assigned to a specific manager who's in charge of that facility. Each issue could have several sub-tasks.

To speed up the sub-task creation, we will set up prepopulation of the basic information in a task form from the parent form of issue, e.g. 'Facility', 'Priority', and 'Assigned to'. 

Lists
--------------------------------------------------

First of all, we will create 3 lists: 

- Facilities; 
- Issues; 
- Tasks (a regular Tasks list).


Facilities list will store the information about the facilities and their managers: 

- Title;
- Manager.


Issues list will contain the following columns: 

- Title (text field);
- Facility (lookup field);
- Manager (people picker field);
- Description (plain text field);
- Priority (choice field).


And the Tasks list will be based on a regular SharePoint Tasks list with just two extra columns: 

- Issue (a lookup field pointing to the Issues list);
- Facility (a lookup field pointing to the Facilities list).

Issue form 
--------------------------------------------------

Here is a simple Issue form containing all the fields from the Issues list plus a 'List or Library' control bound to the Tasks list and displaying issue's subtasks.

|pic1|

.. |pic1| image:: ../images/how-to/pass-values/pass-values-1.png
   :alt: Issue form 

To be able to pass value from a parent form to a child, we need to define *fd* globally in the parent form with. To be able to pass the value from a parent form to a child form, we need to define *fd* globally in the parent form with the code: 

.. code-block:: javascript

    window.fd = fd; 


|pic2|

.. |pic2| image:: ../images/how-to/pass-values/pass-values-2.png
   :alt: window.fd

Since each facility has a manager, we'll populate the Manager field when the Facility changes. To do this, we will add the following code into JavaScript editor: 

.. code-block:: javascript

    window.fd = fd; 

    fd.spRendered(function() { 
        
        fd.field('Facility').$on('change', function () { 
            fd.field('Manager').value = fd.field('Facility').value.Manager.EMail; 
        }) 
    }); 

Task form 
--------------------------------------------------

Here is a form of the Tasks list: 

|pic3|

.. |pic3| image:: ../images/how-to/pass-values/pass-values-3.png
   :alt: Task form

Here we will populate Priority, Facility, and Assigned To fields with values from the parent form. 

To get access to the parent form's fields, we will use 'window.top' property which returns the topmost window object. Here is our code that we put to the task form: 

.. code-block:: javascript

    fd.spRendered(function() {
        var parentForm = window.top.fd;
        
        if (parentForm) {

            //Set field values with the values from the parent on form load
            fd.field('Facility').value = parentForm.field('Facility').value.ID;
            fd.field('Priority').value = parentForm.field('Priority').value;
            fd.field('AssignedTo').value = parentForm.field('Manager').value; 
            
            //Disable Location field
            fd.field('Facility').disabled = true;
        }
    }); 