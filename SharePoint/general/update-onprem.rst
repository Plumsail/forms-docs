.. title:: Update Plumsail Forms On-Premises solution

.. meta::
   :description: How to download and install an update for the On-Premises installation of Plumsail Forms

Update Plumsail Forms On-Premises solution
==================================================

.. contents:: Contents:
 :local:
 :depth: 1

Server package
--------------------------------------------------
First of all, |Download setup file| and run it on one of the servers in your Sharepoint 2019 farm as Farm Administrator. Follow wizard steps.

.. Note:: Alternatively, :doc:`use WSP package </install-wsp>` to install the latest version.

.. |Download setup file| raw:: html

   <a href="https://plumsail.com/forms/start-trial/" target="_blank">download setup file</a>

After the package installation, go to Site collection features and re-activate (de-activate and activate again) Plumsail Forms feature:

|pic1|

.. |pic1| image:: /images/startSP/plumsailFormsFeature.png
   :alt: Plumsail Forms feature

App catalog
--------------------------------------------------
Navigate to the a list and click Design Forms:

|pic3|

.. |pic3| image:: /images/startSP/runFormsFromRibbon.png
   :alt: Run Forms from Ribbon

Download the latest App package:

|pic4|

.. |pic4| image:: /images/startSP/download2019Package.png
   :alt: Download 2019 App package

Navigate to the app catalog: **delete** the existing package, upload the new one and deploy it globally (check **Make this solution available to all sites in the organization**):

|pic6|

.. |pic6| image:: /images/startSP/package2019.png
   :alt: Make this solution available to all sites in the organization

Final steps
--------------------------------------------------
Download and install the new editor desktop app:

|pic7|

.. |pic7| image:: /images/startSP/download2019Designer.png
   :alt: Download and install the designer

Clear browser's cache to make sure all changes have applied:

|pic8|

.. |pic8| image:: /images/startSP/startSP-clear-cache.png
   :alt: Clear browser's cache