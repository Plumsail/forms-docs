.. Forms documentation master file, created by
   sphinx-quickstart on Tue Apr 12 16:52:35 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Plumsail Forms for public web forms
=================================================

.. toctree::
  :hidden:

  Table of contents <self>

.. container:: pl-left-column

      .. toctree::
            :caption: Getting started
            :maxdepth: 1

            Designing forms <./design>
            Sharing forms <./sharing>
            Collecting form data <./submissions>
            Handling form data in Power Automate <./microsoft-flow>
            Handling form data in Zapier <./zapier>

      .. toctree::
            :caption: General
            :name: generaltoc
            :maxdepth: 1
            :titlesonly:
            
            Version history <general/version-history>
            Roadmap <general/roadmap>  
            YouTube channel <https://www.youtube.com/channel/UCR7Ni67GwQ228j9MuGq-39A>
            Licensing <./licensing>
            Renew or upgrade subscription <general/upgrade-renew>  
            Privacy policy <general/privacy-policy> 
            Data protection and security <general/data-security>

      .. toctree::
            :caption: Designer
            :maxdepth: 1
            :titlesonly:

            Toolbar actions <designer/toolbar-actions>
            Themes <designer/themes>
            Containers <designer/containers>
            Controls <designer/controls>
            Fields <designer/fields>

      .. toctree::
            :caption: JavaScript framework 
            :maxdepth: 1
            :titlesonly:

            Introduction <javascript/general>
            Manager <javascript/manager>
            Containers <javascript/containers>
            Controls <javascript/controls>
            Fields <javascript/fields>

      .. toctree::
            :caption: Integrations
            :maxdepth: 1
            :titlesonly:

            integrations/saving-sharing
            integrations/document-generation
            integrations/collaboration
            integrations/crm
            integrations/social-networks

.. container:: pl-right-column

      .. toctree::
            :caption: Complex layouts 
            :maxdepth: 1
            :titlesonly:

            Organize content with Grids <how-to/grid-advantages>
            Manipulate Tabs, Accordions, and Wizards with JavaScript <how-to/conditional-containers>
            Align fields to the right for Arabic, Hebrew and other languages <how-to/right-left>
      
      .. toctree::
            :caption: Working with fields in JavaScript 
            :maxdepth: 1
            :titlesonly:

            Populate, hide, disable, make mandatory fields <how-to/conditional-fields>
            Date and Time: calculate difference, adjust values <how-to/manipulate-date-field>
            Data Table: populate cells, calculate totals, duplicate rows <how-to/data-table-cases>

      .. toctree::
            :caption: Advanced controls in Power Automate
            :maxdepth: 1
            :titlesonly:

            Convert Data Table into PDF document  <how-to/data-table-flow>
            Convert Data Table into HTML document <how-to/data-table-convert-html>
            Save Data Table rows to SharePoint list <how-to/data-table-to-sp>
            Save Data Table, Ink Sketch, Likert Scale to SharePoint columns <how-to/save-controls-to-sp>
            Save Data Table rows to Excel or Google Sheets <how-to/excel-datatable>

      .. toctree::
            :caption: Advanced controls in Zapier
            :maxdepth: 1
            :titlesonly:

            Save Data Table rows to Google Sheets <how-to/zapier-googlesheets>
            Save Likert Scale answers to Excel <how-to/zapier-excelchart>

      .. toctree::
            :caption: Provisioning public forms with NuGet package
            :maxdepth: 1
            :titlesonly:

            Create and provision web forms programmatically <how-to/provision-api>
            how-to/provision-example

      .. toctree::
            :caption: Examples
            :maxdepth: 1
            :titlesonly:

            Expense reimbursement form <examples/expense-reimbursement>
            Online quiz and graphic results <examples/build-excel-charts>
            Online survey with Likert Scale and real-time charts <examples/zapier-excelchart>
            Making handwritten notes on images <examples/notes-on-an-image>
            Embedding forms into Microsoft Teams <examples/ms-teams>