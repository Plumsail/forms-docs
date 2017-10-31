Manager
==================================================

fd
--------------------------------------------------
**fd** is a Forms designer manager global variable. Whenever you want to use custom methods on the form, you need to call the manager first. 

Plumsail Forms Events
**************************************************
These events can be executed from JavaScript editor for Plumsail Forms:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   - Event
        - Description
        - Example
    *   - **beforeCreate()**
        - This event is executed prior to form creation
        - fd.beforeCreate((r) => { alert('beforeCreate'); console.log(r); });
    *   - **created()**
        - This event is executed as soon as the form is created
        - fd.created((r) => { alert('created'); console.log(r); });
    *   - **beforeRender()**
        - This event is executed before the form starts rendering, not for Sharepoint
        - fd.beforeRender((r) => { alert('beforeRender'); console.log(r) });
    *   - **rendered()**
        - This event is executed before the form starts rendering, not for Sharepoint
        - fd.rendered((r) => { alert('rendered'); console.log(r); });
    *   - **beforeSave()**
        - This event is executed before the form gets saved, not for Sharepoint
        - fd.beforeSave((r) => { alert('beforeSave'); console.log(r) });
    *   - **saved()**
        - This event is executed as soon as the form is saved, not for Sharepoint
        - fd.saved((r) => { alert('saved'); console.log(r); });

Modern Sharepoint Forms Events
**************************************************
These events can be executed from JavaScript editor for Modern Sharepoint Forms:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20

    *   - Event
        - Description
        - Example
    *   - **beforeCreate()**
        - This event is executed prior to form creation
        - fd.beforeCreate((r) => { alert('beforeCreate'); console.log(r); });
    *   - **created()**
        - This event is executed as soon as the form is created
        - fd.created((r) => { alert('created'); console.log(r); });
    *   - **spBeforeRender()**
        - This event is executed before the Sharepoint form starts rendering
        - fd.spBeforeRender((r) => { alert('spBeforeRender'); console.log(r) });
    *   - **spRendered()**
        - This event is executed before the Sharepoint form starts rendering
        - fd.spRendered((r) => { alert('rendered'); console.log(r); });
    *   - **spBeforeSave()**
        - This event is executed before the Sharepoint form gets saved
        - fd.spBeforeSave((r) => { alert('spBeforeSave'); console.log(r) });
    *   - **spSaved()**
        - This event is executed as soon as the Sharepoint form is saved
        - fd.spSaved((r) => { alert('spSaved'); console.log(r); });
