.. Forms documentation master file, created by
   sphinx-quickstart on Tue Apr 12 16:52:35 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Plumsail Forms for SharePoint
=================================================

.. toctree::
  :hidden:

  Table of contents <self>

.. container:: pl-left-column

      .. toctree::
            :caption: Getting started
            :maxdepth: 1
            :titlesonly:

            Installation to SharePoint Online (Office 365) <./installation-sp>
            Installation to SharePoint 2019 <./installation-2019>
            Designing forms <./design-sp>

      .. toctree::
            :caption: General
            :name: generaltoc
            :maxdepth: 1
            :titlesonly:
            
            Version history (SharePoint Online) <general/version-history> 
            Version history (SharePoint 2019) <general/version-history2019> 
            Roadmap <general/roadmap> 
            YouTube channel <https://www.youtube.com/channel/UCR7Ni67GwQ228j9MuGq-39A>
            Licensing <./licensing-sp>
            Privacy policy <general/privacy-policy>
            Data protection and security <general/data-security>

      .. toctree::
            :caption: Designer
            :maxdepth: 1
            :titlesonly:

            Ribbon actions <designer/ribbon-actions> 
            Form sets <designer/form-sets> 
            Containers <designer/containers> 
            Controls <designer/controls> 
            SharePoint fields <designer/fields-sp> 
            Common fields <designer/fields>
            Field customizers <designer/customizers.rst>
            SharePoint web part <designer/web-part> 
            SharePoint form panel <designer/panel> 
            

      .. toctree::
            :caption: JavaScript framework 
            :maxdepth: 1
            :titlesonly:

            Introduction <javascript/general> 
            Manager <javascript/manager> 
            Containers <javascript/containers> 
            Controls <javascript/controls> 
            SharePoint fields <javascript/fields-sp> 
            Common fields <javascript/fields> 
            Toolbar <javascript/toolbar> 
            Dialog <javascript/dialog> 
      
      .. toctree::
            :caption: Provisioning forms
            :maxdepth: 1
            :titlesonly:

            Provisioning API <provision/general> 
            Provisioning forms (samples) <provision/provision>
            Provisioning Form sets and Panel (samples) <provision/provision-fs>

      .. toctree::
            :caption: Examples
            :maxdepth: 1
            :titlesonly:

            Ticket management system <examples/ticket-management>
            Dynamic form for a user group <examples/dynamic-form-based-on-membership>
            Conference room reservation system <examples/reservation-system>
            Discussion within a SharePoint form <examples/add-discussion>
            Version history within a SharePoint form <examples/version-history>
            Organizing related docs in libraries and folders <examples/create-folder>
            Duplicate item button for List or Library <examples/list-or-library-duplicate>
            Embedding forms into Microsoft Teams <examples/ms-teams>
            Transferring new form page to another location <examples/newform-page>
      

.. container:: pl-right-column
      
      .. toctree::
            :caption: Complex layouts
            :maxdepth: 1
            :titlesonly:

            Organize content with Grids <how-to/grid-advantages> 
            Manipulate Tabs, Accordions, and Wizards with JavaScript <how-to/conditional-containers> 
            Align fields to the right for Arabic, Hebrew and other languages <how-to/right-left> 
            Restore previous versions of a form <how-to/form-versions> 

      .. toctree::
            :caption: Personal forms
            :maxdepth: 1
            :titlesonly:

            Personalize form based on user group in SharePoint or Azure AD <how-to/forms-for-groups>
            Open edit form by default for a user group <how-to/edit-form>
            Create forms in multiple languages <how-to/language>

      .. toctree::
            :caption: Navigation between forms
            :maxdepth: 1
            :titlesonly:

            Redirect user after form submission <how-to/redirect-sp-save>
            Open any form in dialog from another form <how-to/form-dialog>
            Generate link to SharePoint form <how-to/link-to-form>

      .. toctree::
            :caption: Working with fields in JavaScript
            :maxdepth: 1
            :titlesonly:

            Populate, hide, disable, make mandatory fields <how-to/conditional-fields>
            Lookup control: cros-site lookup, related items from another site <how-to/csl>
            Date and Time: calculate difference, adjust values <how-to/manipulate-date-field>
            Data Table: populate cells, calculate totals, duplicate rows <how-to/data-table-cases>    
            Get field values of a parent form from a dialog <how-to/pass-values>
            Populate common Drop Down field with values from a SharePoint list <how-to/populate-dropdowns>
            Populate Drop Down column of Data Table with values from a SharePoint list <how-to/dynamic-datatable>
            Populate fields with profile information <how-to/populate-user-info>

      .. toctree::
            :caption: List or Library control
            :maxdepth: 1
            :titlesonly:

            Create forms with related items or documents <how-to/child-parent-form>
            Change the root folder dynamically <how-to/root-folder>
            Filter related items or documents dynamically <how-to/caml-filter>
            Update properties of uploaded files <how-to/document-meta>
            Add or customize buttons in the toolbar <how-to/list-or-library-buttons>
            Handle fields in inline editing mode <how-to/list-or-library-inline>
            Customize view of columns <how-to/list-or-library-columns>

      .. toctree::
            :caption: SharePoint Lookup field
            :maxdepth: 1
            :titlesonly:

            Customize appearance of search results <how-to/lookup-view>
            Filter by another field: Lookup, Person, Choice <how-to/lookup-filter>
            Filter by another field with JavaScript <how-to/lookup-cascading>
            Search and filter large lists (more than 5,000 Items) <how-to/lookup-5k>

      .. toctree::
            :caption: Generating PDF documents
            :maxdepth: 1
            :titlesonly:

            Save SharePoint form as PDF <how-to/export-to-pdf-setup>
            Generate PDF from DOCX template with Plumsail Processes <how-to/create-pdf-processes>
            Generate PDF from DOCX template with Word Online (Business) <how-to/create-pdf-power-automate>


      .. toctree::
            :caption: Integration with Power Automate
            :maxdepth: 1
            :titlesonly:

            Send e-mail notification after submitting SharePoint form <how-to/flow>
            Start flow after submitting SharePoint form and wait for results <how-to/flow-edit-display>
            Start flow from List or Library and pass selected items <how-to/list-or-library-export>