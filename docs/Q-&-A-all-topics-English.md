# Questions & answers related to AIS, Postman Samples, RA, MobileID, Billing, etc.

**1. Company X now wants to switch from AIS Preprod to AIS Prod because they have finished testing. Can you please tell me
From a contractual point of view, which steps company X has to take and how it works in general, what has to be signed, etc.?**

* Sales, in this case Marcel (Marcel.Kurz@swisscom.com), instructs us to draw up the desired contract:
* https://collaboration.swisscom.com/communities/swisscom-digital-certificate-services/SDCS_Collab/Forms/AllItems.aspx?RootFolder=%2Fcommunities%2Fswisscom%2Ddigital%2Dcertificate%2Dservices%2FSDCS%5FC5FAIS%10 5FOperations% 2FAuftr% C3% A4geSales & FolderCTID = 0x0120009F4F9BE777BD6F4F823759ED2E7DEC76 & View =% 7BE5CCB974% 2D9EE8% 2D4087% 2DAE09% 2DB90602A14D5E% 7D

* Furthermore, it must be clarified whether company X has a test account first.

 
**2. Billing models for the MobileID / AIS user: how does it work? Which models are there? How is the signature flat rate used? Can
Does the user continue to use the flat rate after signing X times (e.g. 3 times)? What are the general conditions regarding posting costs,
how does that work specifically?**

* The customer chooses the billing variant in the corresponding contract, but the option of billing per user / month is only available to resellers or when ordering via partners, for end customers there is only "per signature". You can find all contract templates in DMIS:
* https://internal.bizdocs.swisscom.com/dmis/start/SitePages/ProductDetail.aspx?PURL=https://internal.bizdocs.swisscom.com/dmis/1000255-All-in-Signing-Service

 
**3. After an AIS signature link has been generated for a user in order to be able to sign with it, how long is this link valid, how many days?**

* If this means the SAS confirmation via SAS, you will find the answer in the Installation Guidance, Section 5.7.3: is configurable, the default is 10 minutes. I don't know more about it, because we don't have a SAS connection for our test environment and therefore don't test it.
* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf
https://trustservices.swisscom.com/downloads/

**4. Are there any costs for video authentication after the user has authenticated himself or after this AIS link has been generated? The company X
wants to know exactly when there will be costs.**

* Please ask Marietta Heule (Marietta.Heule@swisscom.com) and / or Marcel (Marcel.Kurz@swisscom.com) in detail.

**5. Please check in the Postman samples that: is replaced with.**

* For example if you have in the Postman Sample: "sc: SignatureStandard" replace it with "sc.SignatureStandard".

 
**6. In the case of a template-based call, a user name must always be given or can a name Place holder be used? Is it later then
Is it possible to add the name when signing?**

* I assume you mean the placeholders for values from the RA evidence in the subject of on-demand signatures. Except for escaping based on the rules for DNs (RFC 2253), this is essentially a text replacement. The templates build on this and provide frequently used subjects with placeholders. You can find our documentation on this in Sections 5.9.2 and 5.9.3 in the Installation Guidance. Regarding your actual question: yes, you can put together a subject with placeholders and then assign your own value to GIVENNAME or CN.
* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf

 
**7. If the user name is passed in a signature request, is the name of the user checked or does it matter? The question goes in the
Direction of what happens if the user has given their name incorrectly. Therefore it is relevant for a successful signature that the name is given correctly, right?**

* There are two tests: On the one hand, the finished subject must match the DN pattern of the on-demand service. If it is a qualified signature, the subject is also given to the RAS for verification ("Evidence Verify Call"). How your DN patterns look like and what exactly the RAS checks can be found here under Smart Registration Service.
* https://trustservices.swisscom.com/downloads/

**8. The object vs. object list problem, has this been resolved in the AIS at the moment? You always have to send an object list with the request, right?
How does it work at the moment?**

* No. Everything is the same in AIS. As far as I know, there is a workaround for this in the PDFBox Client.
* It's not about the request, but about the response. In the scheme for this there are some properties that are a list - for example the list of the created signatures or the list of OCSP and CRL. Depending on whether it contains zero, one or more elements, the property is serialized in JSON as a single value or as a list of values. But it should always be a list. If I want to work with the respective property as a client, I always have to first check whether it is a single value or a list of values. That's not the end of the world, but it's cumbersome and annoying. This problem does not exist with SOAP.

 
**9. With a signature, is it possible for the user to indicate whether he wants to become EIDAS or ZertES? I can't find it in the JSON AIS samples we have.
How is it currently implemented in the AIS? A short description would help me a lot.**

* The client selects an on-demand service for the signature. This refers to a CA server. The level of assurance and the jurisdiction for the signature are derived from the name of this CA server. How is described, among other things, in the Admin UI User Manual, Section 3.4.1. The "Data Flow Issues" currently being processed by us want to change exactly that, so that these properties are no longer defined by naming conventions, but instead end up explicitly in the database. According to the previous statement, you cannot select EIDAS or ZertES, it will certainly be adjustable later.

**10. POC implementation, what do I have to pay attention to?**

* I have to do a video registration, so I can only sign in the EU.
* This is done here.
* https://trustservices.swisscom.com/en/smart-registration-service/
* I have to register in the Swisscom Shop, so I can then also sign in Switzerland.
