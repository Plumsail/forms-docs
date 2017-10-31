Methods
==================================================

Fields
--------------------------------------------------

General methods
**************************************************
These methods are applicable to most fields:

.. list-table::
    :header-rows: 1
    :widths: 10 20 20
        
    *   - Method
        - Description
        - Examples
    *   - **field(FieldName).title**
        - Allows to get or set field's title
        -   * fd.field('TextBox').title;
            * fd.field('TextBox').title = "New Title";
    *   - **field(FieldName).required**
        - Returns true if the field is required, allows to set field required or not required
        -   * fd.field('TextBox').required;
            * fd.field('TextBox').required = true;
    *   - **field(FieldName).value**
        - Allows to get or set field's value
        -   * fd.field('TextBox').value;
            * fd.field('TextBox').value = 'Hello, world!';
    *   - **field(FieldName).disabled**
        - Returns true if the field is disabled, allows to disable field, making it essentially Read-only
        -   * fd.field('TextBox').disabled;
            * fd.field('TextBox').disabled = true;
    *   - **CHANGE**
        - Something about detecting CHANGE
        -   * EXAMPLE #1;
            * EXAMPLE #2;