.. title:: Configure lookup fields pointing to very large lists

.. meta::
   :description: How to add support to lookup fields that point to very large lists with over 5,000 items with indexed columns

How to configure lookup fields pointing to large lists with more than 5000 items
===============================================================================================

Default SharePoint Lookups do not support large lists with more than 5,000 Items, but Plumsail Forms' Lookups will work with these large Lists.

But choosing correct item among more than 5,000 choices is not an easy task. That's why, our Lookups also support search and filtering.

|pic1|

.. |pic1| image:: ../images/how-to/lookup-5k/threshold.png
   :alt: Threshold

.. contents:: Contents:
 :local:
 :depth: 1

Index Columns
--------------------------------------------------
How to configure Source list, so it can be searched and filtered? It's very easy.
All you have to do is index Source list's columns that you intend to filter. 

Read more about indexing columns in |Microsoft's instruction|.

You need to index **all columns** that you intend to use with the Lookup filtering and search. 

If you only want to search items by Title, then only the Title needs to be indexed.

|pic2|

.. |pic2| image:: ../images/how-to/lookup-5k/title.png
   :alt: Title Indexed

If you follow our :doc:`instruction for Cascading Dropdowns </how-to/lookup-cascading>`, then both Category and Product columns need to be indexed in the Source list.

.. |Microsoft's instruction| raw:: html

   <a href="https://support.office.com/en-us/article/add-an-index-to-a-sharepoint-column-f3f00554-b7dc-44d1-a2ed-d477eac463b0" target="_blank">Microsoft's instruction</a>

Result
--------------------------------------------------
Here I have a large list with over 5,000 Items:

|pic4|

.. |pic4| image:: ../images/how-to/lookup-5k/large.png
   :alt: Large List

And here's a Lookup to that List, which I can search as I see fit after indexing its Title:

|pic5|

.. |pic5| image:: ../images/how-to/lookup-5k/search.png
   :alt: Lookup to a Large List