Responsive UI
==================================================


Grid System
--------------------------------------------------

Plumsail Forms utilize `Bootstrap Grid System <https://v4-alpha.getbootstrap.com/layout/grid/#how-it-works>`_. As such, every element on the form, including Containers, Controls and Fields, has Parent Grid properties by default.

Parent Grid properties
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
    :header-rows: 1
    :widths: 10 40
        
    *   - Property
        - Description
    *   - Width
        - Determines how much width an element takes, where 12 is full grid and other values represent smaller portions of the grid. If you add new elements or adjust Width of other elements and run out of space, Width of elements to the right will automatically adapt in the designer, so make sure that your elements don't take more than 12 total.
    *   - Offset
        - Determines how much of an offset element gets from the left. The offset number also determines how much of the total grid space offset takes, where 6 is equal to half the grid. Setting offset will also affect total available Width for the element, and if not enough space left, it will automatically adjust to be smaller.
    *   - Padding
        - Allows you to give extra padding to a particular element from any side, Padding is set in pixels.
    *   - CSS Class
        - Allows you to give custom CSS classes to the grid cell which then can be used in CSS or with JavaScript. Multiple classes need to be separated with spaces.
    *   - Style
        - Allows you to give custom style settings to the grid cell. Works as a style attribute of an HTML tag, doesn't require any selectors to work.

You are not limited to one grid per Form either. By placing Grid container inside the form, you are technically inserting one grid within another and then can layout elements within second grid, which will be constrained by its own Parent Grid. Similar happens when you place Tab Control or Accordion inside the form, they also have grid inside of them. So, despite Parent grid only having 12 options for Width property, you can adjust your layout precisely by using multiple grid containers.