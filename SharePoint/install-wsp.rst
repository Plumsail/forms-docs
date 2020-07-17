.. title:: Plumsail Forms WSP installation for SharePoint 2019

.. meta::
   :description: How to install Forms WSP package to SharePoint On-Premises with SharePoint Management Shell

WSP installation for SharePoint 2019
==================================================

|Download wsp-package| and place it to one of the servers in your Sharepoint 2019 farm. Run Sharepoint Management Shell as administrator:

.. |Download wsp-package| raw:: html

   <a href="https://plumsail.com/forms/start-trial/" target="_blank">Download wsp-package</a>

|WspInstallation1|

.. |WspInstallation1| image:: /images/startSP/WspInstallation1.png
   :alt: Launch SharePoint Management Shell

|WspInstallation2|

.. |WspInstallation2| image:: /images/startSP/WspInstallation2.png
   :alt: Run as administrator

Print:

.. code-block:: c#

    Add-SPSolution <path to wsp-package>

|Powershell|

.. |Powershell| image:: /images/startSP/powershell.png
   :alt: Powershell add solution

Open Central Administration as administrator → System Settings → Manage farm solutions. Select **Plumsail.Forms.SP2019.wsp** and press Deploy Solution link:

|Deploy|

.. |Deploy| image:: /images/startSP/deploySolution.png
   :alt: Deploy solution

Go to your application. Select Site Settings item in the root of the site collection. Choose Site collection features in Site Collection Administration section:

|siteCollectionFeatures|

.. |siteCollectionFeatures| image:: /images/startSP/siteCollectionFeatures.png
   :alt: Site Collection Features

Activate Plumsail Forms feature:

|feature|

.. |feature| image:: /images/startSP/plumsailFormsFeature.png
   :alt: Plumsail Forms feature

Then go to any of the lists on the Site Collection where you've activated Plumsail Forms feature, open List View in Modern UI and click Design Forms button:

|Ribbon|

.. |Ribbon| image:: /images/startSP/runFormsFromRibbon.png
   :alt: Run Forms from Ribbon

To complete installation, follow the instruction steps described there, and :ref:`install-app-package2019`.
