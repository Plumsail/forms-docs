Fields
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

General Info
-------------------------------------------------------------
Fields are primary input elements on the Form. 
Fields are being filled by the user and store their data in user's session storage and once the form is submitted, their contents are handled by MS Powerautomate.
SharePoint Fields are saved directly to SharePoint List/Library.

Basic properties
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Most fields have following settings:

General

.. list-table::
    :widths: 10 40

    *   - Name
        - Setting utilized by many elements. Name is similar to ID, it's a unique identifier for the element.
    *   - Required
        - Select if the field is required to submit the form or not.
    *   - Orientation
        - Select if the title is displayed on the left from field or on top of it, to the left. Might automatically switch if not enough space.
    *   - Class
        - Give CSS Class to the element, in order to apply JavaScript or CSS Style to it. Can give multiple classes separated by spaces to one element.
    *   - Style
        - Allows you to give specific element certain style. No need to use selectors, simply add CSS rules to this setting.

Title

.. list-table::
    :widths: 10 40

    *   - Text
        - Select the displayed title for the field.
    *   - Visible
        - Select if the title is visible or not.
    *   - Width
        - Select the width of the title.
    *   - Font Size
        - Select font size of the title.
    *   - Font Style
        - Select if the title is in italics or not.
    *   - Font Weight
        - Select if the title is bold or not.
    *   - Font Color
        - Select font color of the title. Can be either selected or manually entered.
    *   - Wrap
        - Select if the title will wrap if it has not enough space or not.

Control

.. list-table::
    :widths: 10 40

    *   - Width
        - Allows you to set the width of the input field manually. Only takes number in pixels, no additional symbols required.
    *   - Hint
        - Allows you to set placeholder value for the text input. Can be used as an example for the users.
    *   - Font Size
        - Select font size for the input.
    *   - Font Style
        - Select if the input is in italics or not.
    *   - Font Weight
        - Select if the input is bold or not.
    *   - Font Color
        - Select font color for the input. Can be either selected or manually entered.