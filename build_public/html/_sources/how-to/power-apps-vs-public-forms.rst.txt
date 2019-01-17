PowerApps vs. Public Forms
==================================================

.. contents:: Contents:
 :local:
 :depth: 1
 
Description
--------------------------------------------------

PowerApps
**************************************************

|PowerApps|, as you probably already now, is a platform developed by Microsoft that allows building mobile apps 
with no need to write your own code (though knowledge of PowerApps syntax can be very helpful at times).

The process is fairly simple and intuitive, though some of the more advanced cases can be hard to figure out. 
Still, the platform is really powerful, and we've discovered these strengths to be at the core of platform's success:

1) Variability and great integration - PowerApps allows you to create all kinds of apps, including Help Desks, Service Desks, Expenses Tracker, Case Management, and much more.
What's really important here - all of these will integrate well with your existing Microsoft's environment, such as Flow, Teams, SharePoint, OneNote and others.

2) Easy to use, but offer complex functionality - while the product is relatively easy to grasp for beginners, but offer a robust toolbox to tackle most specific uses cases.
While it's not necessary to write any actual code, chances are that you will need to use PowerApps syntax to attain the results you are looking for.

3) Mobile integration - let's face, this is definitely the main appeal of the platform. While it's possible to use PowerApps on PCs, they offer much better experience on phones
and tablets, allowing many users to move away from the PCs and use their phones or tablets when working with PowerApps.

|pic1|

.. |pic1| image:: ../images/how-to/power-apps/power-apps.png
   :alt: PowerApps

.. |PowerApps| raw:: html

   <a href="https://powerapps.microsoft.com/en-us/" target="_blank">PowerApps</a>

Forms
**************************************************

So, why are we talking about PowerApps? Because, our product - |Forms|, allows you to achieve the same goals as PowerApps, 
and in many cases allows even to work around the limitations of the platform.

.. |Forms| raw:: html

   <a href="https://plumsail.com/forms" target="_blank">Forms</a>

It's hard to pinpoint all the differences between the two, and have a fixed list of what advantages you can get with each one, as both PowerApps and our Forms are in active 
development, so we can expect new features to come to both. But we've tried to collect the information on how it is today, 
and what benefits you would get by using our product over PowerApps.

|pic2|

.. |pic2| image:: https://static.plumsail.com/wp-content/themes/plumsail/assets/images/content/product/forms/public-forms-designer.png
   :alt: Plumsail Forms

Truly public forms
--------------------------------------------------
While PowerApps allows creation powerful of apps, there is currently no easy way to share these apps with people outside of Office365 ecosystem. 
That means that while sharing with the users inside your organization might not be hard to implement (provided they all have an Office365 account), it makes sharing
PowerApps much harder with users outside of the organization, for example, partners or customers.

Contrast this with Public Web Forms you can build with Plumsail Forms. Not only can you easily add these forms to your Office365 environment, 
such as a tab in MS Teams or a SharePoint page, but you can also publish these forms ANYWHERE in the web, for instance, on your own website. 

All the data is collected by |Flow| (alternatively, you can use |Zapier|), and then integrated into your own environment as you see fit. All you have to do is:
design a form, configure a Flow, publish just a few lines of HTML widget to any webpage - and users would be able to submit data, no need to login at all!
This data can then be used in SharePoint, stored in SQL, sent in an email, or otherwise processed by Flow, as you see fit.

|ExampleForm|

.. |ExampleForm| raw:: html

   <h3>An example form</h3>
   <style>
   .fd-form .btn-primary {background-image: none;}
   </style>
    <script type="text/javascript" src="https://forms.plumsail.com/widget/1.0.3/app.js"></script>
    <div id="plumsail-form"><div class="fd-form-loading" /></div>
    <script type="text/javascript">
        var fd = new Plumsail.Form("#plumsail-form", "50baacee-3b99-4ccd-882e-2ebffa83b213");
    </script>        </div>

.. |Zapier| raw:: html

   <a href="https://zapier.com/" target="_blank">Zapier</a>

.. |Flow| raw:: html

   <a href="https://flow.microsoft.com/en-us/" target="_blank">Microsoft Flow</a>

Responsive very complex forms out of box
-------------------------------------------------- 
Designing forms with PowerApps web editor is not hard, true. And you can set up whether you create a phone or a tablet form, and adjust it accordingly.

But if you worked with PowerApps before, you know it can still be a struggle to achieve the precise effect you are going for. 
Implementing containers, such as Tabs or Accordions would take a lot of time, and you would probably need to separate one form 
into multiple parts, and tie them together with custom logic.

Nothing like this is necessary with Plumsail Forms. First of all, forms are responsive by default - they're based on Bootstrap Grid, 
and will scale depending on the size of the screen. For the more complex forms, you can configure different layouts for PC, Tablet or Phone - all within one form,
simply changing how the form will be presented on different devices.

Secondly, you can create really complex forms with very little code, if any. Split form into parts with Tabs, Accordion, or even Wizard container, and drag and drop 
the fields inside - it all works straight away.

|pic3|

.. |pic3| image:: ../images/how-to/power-apps/mobile-public-forms.gif
   :alt: Mobile Public Forms

Custom controls and rich JS API 
--------------------------------------------------
To make your forms truly suit your needs perfectly, we've included a wide selection of custom containers, controls, and fields. Not only these are available out of the box,
without the need for external applications, but we also provide powerful JavaScript API to work with the form and with the elements on it.

For example, you can include a DataTable, control which allows users to add rows to it. Each row has a set of columns which you set up in the designer. You can make certain
columns mandatory, while others optional. You can also add other limitations to user input, or calculate some data, for example, Tax and Total values based on input in DataTable.

Alternatively, you can use Wizard Conainer, and separate your form into steps, where users must complete each step before moving on to the next. With the ability to write
custom validators for each field, you can come up with unique interaction for each use case planned.

Much more customization is available, both directly in the designer, and via the use of custom JS API, but it would take too long to describe 
all the potential use cases in one article. While PowerApps syntax comes with variety of functions, it still is not as powerful as use of JavaScript could be.

|pic4|

.. |pic4| image:: https://static.plumsail.com/wp-content/themes/plumsail/assets/images/content/product/forms/public-forms-wizard-control.png
   :alt: Plumsail Forms Custom Controls

Pricing and Licensing
--------------------------------------------------
While PowerApps are licensed primarily per user, Public Forms offer a subscription license, with |Forms Plans| depending on the amount of submissions per month. 

So, if your Forms need to be used by a large number of users, it would definitely be more price efficient to use Plumsail Forms, 
as you would only pay for submissions, not for users. And even if the number of users is limited, you might find that our prices would most likely give you an edge over PowerApps,
so it heavily depends on which products functionality suits you best.

Public Forms are published on a webpage, which could be either public or private, and would work well with both mobile and PC screens, so it's not suited for app development,
but if you are looking for mobile-friendly forms to connect to MS Flow - give |Try Forms|.

.. |Try Forms| raw:: html

   <a href="https://auth.plumsail.com/account/Register?ReturnUrl=https://account.plumsail.com/forms/intro&_ga=2.32491006.1320632069.1543243232-357820995.1542205926" target="_blank">Public Forms a try</a>

.. |Forms Plans| raw:: html

   <a href="https://plumsail.com/forms/store/public-forms/" target="_blank">several plans</a>