.. title:: Populate SharePoint form fields with profile information

.. meta::
   :description: Use JavaScript to populate fields with information about the current user such as name, job title, department, phone, manager name and more

How to populate SharePoint form fields with profile information
=========================================================================

In this article, we will show you how to retrieve information from a user profile and prepopulate form fields with it. 

|pic0|

.. |pic0| image:: ../images/how-to/populate-user-info/populate-user-info-0.gif
   :alt: preview

Editing user profile properties
--------------------------------
You can see and edit user profile properties in the "SharePoint Admin Centre > Classic features > User Profiles > Manage User Profiles > Edit User Profile".

.. Note:: Administrators can create custom profile properties, populate them with PowerShell, and configure synchromization with Active Directory.

For more information, check out |Microsoft's article on how to manage user profile properties|.

.. |Microsoft's article on how to manage user profile properties| raw:: html

    <a href="https://docs.microsoft.com/en-us/sharepoint/manage-user-profiles" target="_blank">Microsoft's article on how to manage user profile properties</a>

Accessing current user profile properties
---------------------------------------------
You can retrieve current user profile properties with the following code:

.. code-block:: javascript

    function updateCurrentUserInfo() {
        pnp.sp.profiles.myProperties.get().then(function(result) {
            
            var props = result.UserProfileProperties;
            
            for (var i = 0; i < props.length; i++) {
                
                switch (props[i].Key) {
                    case 'Manager':
                        fd.field('Manager').value = props[i].Value;
                        break;
                    
                    case 'Department':
                        fd.field('Department').value = props[i].Value;
                        break;
                    
                    case 'Title':
                        fd.field('JobTitle').value = props[i].Value;
                        break;
                    
                    case 'CellPhone':
                        fd.field('Mobile').value = props[i].Value;
                }
            } 
        });
    } 
    
    fd.spRendered(function() {
        //executes updateCurrentUserInfo on form load
        updateCurrentUserInfo();
    }); 

Accessing Person field user profile properties
------------------------------------------------
You can also retrieve user profile properties for a user selected in the user field:

.. Note: Form user must have access to these properties to retrieve them successfully

.. code-block:: javascript

    function updateUserInfo() {
        var employee = fd.field('PersonFieldName').value;

        if (employee && employee.Key){
            pnp.sp.profiles.getPropertiesFor(employee.Key).then(function(result) {
            
                var props = result.UserProfileProperties;
                
                for (var i = 0; i < props.length; i++) {
                    
                    switch (props[i].Key) {
                        case 'Manager':
                            fd.field('Manager').value = props[i].Value;
                            break;
                        
                        case 'Department':
                            fd.field('Department').value = props[i].Value;
                            break;
                        
                        case 'Title':
                            fd.field('JobTitle').value = props[i].Value;
                            break;
                        
                        case 'CellPhone':
                            fd.field('Mobile').value = props[i].Value;
                    }
                } 
            });
        }
    } 
    
    fd.spRendered(function() {
        //executes updateUserInfo on field change
        fd.field('PersonFieldName').$on('change', updateUserInfo);
    }); 
