SharePoint 2019 Installation (On-Premises)
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

Install Farm Solution
------------------------------------------------------------
|Download setup file| and run it on one of the servers in your Sharepoint 2019 farm as Farm Administrator. Follow wizard steps.

.. |Download setup file| raw:: html

   <a href="https://plumsail.com/forms/start-trial/" target="_blank">Download setup file</a>

Make sure that Plumsail Forms feature is activated at the site collection level of the target site:

|pic1|

.. |pic1| image:: /images/startSP/plumsailFormsFeature.png
   :alt: Plumsail Forms feature

Then go to any of the lists on the Site Collection where you've activated Plumsail Forms feature, open List View in Modern UI and click Design Forms button:

|pic3|

.. |pic3| image:: /images/startSP/runFormsFromRibbon.png
   :alt: Run Forms from Ribbon

To complete installation, follow the instruction steps described there.

Upload package to App Catalog
------------------------------------------------------------
|Create an App Catalog| for the target web application: go to Central Administration → Apps → Manage App Catalog:

|pic2|

.. |pic2| image:: /images/startSP/createAppCatalog.png
   :alt: Create App Catalog

.. |Create an App Catalog| raw:: html

   <a href="https://docs.microsoft.com/en-us/sharepoint/administration/manage-the-app-catalog" target="_blank">Create an App Catalog</a>

Next thing you'll need to do, if you've created the App Catalog already, is download the app package by clicking on the link:

|pic4|

.. |pic4| image:: /images/startSP/download2019Package.png
   :alt: Download 2019 App package

Then, go to your App Catalog and upload the package there by dragging and dropping it:

|pic5|

.. |pic5| image:: /images/startSP/upload2019Package.png
   :alt: Upload 2019 App package

Make sure to check **Make this solution available to all sites in the organization** - it's very important for the app to work properly:

|pic6|

.. |pic6| image:: /images/startSP/package2019.png
   :alt: Make this solution available to all sites in the organization

Download designer and start designing forms for SharePoint
------------------------------------------------------------
Once you've added and distributed app across your sites using App catalog, 
it is time to download Forms Designer and start using it. Go back to the Design Forms page and download the desktop application:

|pic7|

.. |pic7| image:: /images/startSP/download2019Designer.png
   :alt: Download and install the designer

Once the designer has downloaded, install it and use to :doc:`design forms for your SharePoint sites </design-sp>`.