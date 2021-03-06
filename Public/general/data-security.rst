.. title:: Data protection and security in Plumsail Forms (public forms)

.. meta::
   :description: How we protect your data - application security, data security, business transactions, GDPR

Data protection and security in Plumsail Forms (public forms)
=================================================================

Privacy Policy
------------------------------
General information about privacy protection can be found in the :doc:`Plumsail Forms Privacy Policy </general/privacy-policy>`.

Application security
------------------------------
Plumsail Forms is hosted in Microsoft Azure. The infrastructure for databases and application servers is managed and maintained by |Azure|.

We are seriously concerned about your security, so, everything from engineering to deployment performed with our highest standards of security. 
Our source code repositories are regularly scanned for security issues and our network is protected by a firewall.

We have a QA department which reviews and test our code for any security vulnerabilities. 
Testing is occurred in a separate environment from production. We don't use any customer's data during testing.

Also, we are using IDS technologies to monitor our network for malicious activity or policy violations.

.. |Azure| raw:: html

   <a href="https://www.microsoft.com/en-us/trustcenter/Security/AzureSecurity" target="_blank">Azure</a>

.. _data-security:

Data security
------------------------------
Plumsail Forms collects very few information about customers - 
only SharePoint Online domain name (for SharePoint License) and |Plumsail Account| email are required for license validation.

After installing Plumsail Forms, the only data that we are gathering from you is application logs from the system.

The data submitted with Public Web Forms is by default stored in Microsoft Azure Storage (you can :doc:`disable this option </submissions>` for any form), |encrypted at REST|. It's not accessible until you login to your |Plumsail Account|, even we don't have access to the stored data. 
Attachments are always stored encrypted at REST, even if the rest of the form data is not stored. Attachments that are older than 30 days are automatically deleted. For the paid plans, this storage can be cleared at any point.

Whenever your data is in transit between you and us, everything is encrypted and sent using HTTPS. Data at rest is encrypted using |AES 256| bit standards (one of the strongest block ciphers available) 
with keys managed by Azure Storage Service Encryption. Data in transit is encrypted with SSL/TLS protocols.

.. |encrypted at REST| raw:: html

   <a href="https://docs.microsoft.com/en-us/azure/security/azure-security-encryption-atrest" target="_blank">encrypted at REST</a>

.. |Plumsail Account| raw:: html

   <a href="https://account.plumsail.com/" target="_blank">Plumsail Account</a>

.. |AES 256| raw:: html

   <a href="https://en.wikipedia.org/wiki/Advanced_Encryption_Standard" target="_blank">AES 256</a>

Business transactions
------------------------------
We protect your billing information. 
All transactions are processed through secure encryption and sensitive data are transmitted, stored and processed on PCI DSS network.

Physical security
------------------------------
Plumsail Forms hosts all data in Microsoft Azure which data centers have been tested for security, availability and business continuity. 
For more information, take a look at |this link|. 
Disaster recovery program ensures that our services will be available or are easily recoverable in the case of any catastrophe.

.. |this link| raw:: html

   <a href="https://www.microsoft.com/en-us/trustcenter/security/azure-security" target="_blank">this link</a>

.. |Disaster recovery program| raw:: html

   <a href="https://azure.microsoft.com/en-us/documentation/articles/resiliency-disaster-recovery-high-availability-azure-applications/" target="_blank">Disaster recovery program</a>

GDPR
------------------------------
Plumsail prioritizes customer trust. We know that customer data is important to our customers’ values and operations. 
That is why we keep it private and safe. 
This section describes our actions to comply with General Data Protection Regulation (“GDPR”), which becomes enforceable on May 25, 2018.

Information that we collect about you as a customer is described in our general |privacy policy|. You, as a customer, have rights and ability to:

- Access your personal data
- Correct errors in their personal data
- Erase your personal data
- Object to processing of your personal data
- Export personal data

Plumsail provides services for form submissions into Power Automate (MS Flow), only the attachments files are stored.
The physical location of those services is inside the Europian Union. 
All data that we process is properly protected and encrypted as described in our :ref:`data-security` and :doc:`privacy </general/privacy-policy>` policies.

Plumsail is implementing necessary data breaches notifications for relevant supervisory authorities and data subjects in accordance with GDPR timeframes.

.. |privacy policy| raw:: html

   <a href="https://plumsail.com/privacy-policy/" target="_blank">privacy policy</a>

Compliance Certifications
------------------------------
Azure data center is certified for ISO 27001, SOC I, II AND III, HIPAA and FedRAMP compliance. Visit |Azure trust center|.

.. |Azure trust center| raw:: html

   <a href="https://azure.microsoft.com/en-us/support/trust-center/" target="_blank">Azure trust center</a>

Get in touch with us
------------------------------
If you have any questions about our security policy, please, feel free to drop a line at support@plumsail.com.
