# Questions & Answers 

  * Please first see the Q&As in the next link afterwards consult these questions and answers below.
  * https://trustservices.swisscom.com/en/faq/

## The Q&As below are related to AIS, Postman Samples, RA Service, MobileID, Billing, and the POC process, etc.

**1. Company X now wants to switch from AIS Preprod to AIS Prod because they have finished testing. Can you please tell me
From a contractual point of view, which steps company X has to take and how it works in general, what has to be signed, etc.?**

<details><summary>
  Click to see the answer. 
  </summary>

* Sales, in this case Marcel (Marcel.Kurz@swisscom.com), instructs us to draw up the desired contract:
* https://collaboration.swisscom.com/communities/swisscom-digital-certificate-services/SDCS_Collab/Forms/AllItems.aspx?RootFolder=%2Fcommunities%2Fswisscom%2Ddigital%2Dcertificate%2Dservices%2FSDCS%5FC5FAIS%10 5FOperations% 2FAuftr% C3% A4geSales & FolderCTID = 0x0120009F4F9BE777BD6F4F823759ED2E7DEC76 & View =% 7BE5CCB974% 2D9EE8% 2D4087% 2DAE09% 2DB90602A14D5E% 7D

* Furthermore, it must be clarified whether company X has a test account first.

</details>

**2. Billing models for the MobileID / AIS user: how does it work? Which models are there? How is the signature flat rate used? Can
Does the user continue to use the flat rate after signing X times (e.g. 3 times)? What are the general conditions regarding posting costs,
how does that work specifically?**

<details><summary>
  Click to see the answer. 
  </summary>

* The customer chooses the billing variant in the corresponding contract, but the option of billing per user / month is only available to resellers or when ordering via partners, for end customers there is only "per signature". You can find all contract templates in DMIS:
* https://internal.bizdocs.swisscom.com/dmis/start/SitePages/ProductDetail.aspx?PURL=https://internal.bizdocs.swisscom.com/dmis/1000255-All-in-Signing-Service

 </details>
 
**3. After an AIS signature link has been generated for a user in order to be able to sign with it, how long is this link valid, how many days?**
<details><summary>
  Click to see the answer. 
  </summary>
 
* If this means the SAS confirmation via SAS, you will find the answer in the Installation Guidance, Section 5.7.3: is configurable, the default is 10 minutes. I don't know more about it, because we don't have a SAS connection for our test environment and therefore don't test it.
* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf
https://trustservices.swisscom.com/downloads/

</details>

**4. Are there any costs for video authentication after the user has authenticated himself or after this AIS link has been generated? The company X
wants to know exactly when there will be costs.**
<details><summary>
  Click to see the answer. 
  </summary>
 
* Please ask Marietta Heule (Marietta.Heule@swisscom.com) and / or Marcel (Marcel.Kurz@swisscom.com) in detail.

</details>

**5. Please check in the Postman samples that: is replaced with.**

<details><summary>
  Click to see the answer. 
  </summary>

* For example if you have in the Postman Sample: "sc: SignatureStandard" replace it with "sc.SignatureStandard".

</details>
 
**6. In the case of a template-based call, a user name must always be given or can a name Place holder be used? Is it later then
Is it possible to add the name when signing?**

<details><summary>
  Click to see the answer. 
  </summary>

* I assume you mean the placeholders for values from the RA evidence in the subject of on-demand signatures. Except for escaping based on the rules for DNs (RFC 2253), this is essentially a text replacement. The templates build on this and provide frequently used subjects with placeholders. You can find our documentation on this in Sections 5.9.2 and 5.9.3 in the Installation Guidance. Regarding your actual question: yes, you can put together a subject with placeholders and then assign your own value to GIVENNAME or CN.
* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf
</details>
 
**7. If the user name is passed in a signature request, is the name of the user checked or does it matter? The question goes in the
Direction of what happens if the user has given their name incorrectly. Therefore it is relevant for a successful signature that the name is given correctly, right?**

<details><summary>
  Click to see the answer. 
  </summary>

* There are two tests: On the one hand, the finished subject must match the DN pattern of the on-demand service. If it is a qualified signature, the subject is also given to the RAS for verification ("Evidence Verify Call"). How your DN patterns look like and what exactly the RAS checks can be found here under Smart Registration Service.
* https://trustservices.swisscom.com/downloads/

</details>

**8. The object vs. object list problem, has this been resolved in the AIS at the moment? You always have to send an object list with the request, right?
How does it work at the moment?**

<details><summary>
  Click to see the answer. 
  </summary>

* No. Everything is the same in AIS. As far as I know, there is a workaround for this in the PDFBox Client.
* It's not about the request, but about the response. In the scheme for this there are some properties that are a list - for example the list of the created signatures or the list of OCSP and CRL. Depending on whether it contains zero, one or more elements, the property is serialized in JSON as a single value or as a list of values. But it should always be a list. If I want to work with the respective property as a client, I always have to first check whether it is a single value or a list of values. That's not the end of the world, but it's cumbersome and annoying. This problem does not exist with SOAP.

</details>
 
**9. With a signature, is it possible for the user to indicate whether he wants to become EIDAS or ZertES? I can't find it in the JSON AIS samples we have.
How is it currently implemented in the AIS? A short description would help me a lot.**

<details><summary>
  Click to see the answer. 
  </summary>

* The client selects an on-demand service for the signature. This refers to a CA server. The level of assurance and the jurisdiction for the signature are derived from the name of this CA server. How is described, among other things, in the Admin UI User Manual, Section 3.4.1. The "Data Flow Issues" currently being processed by us want to change exactly that, so that these properties are no longer defined by naming conventions, but instead end up explicitly in the database. According to the previous statement, you cannot select EIDAS or ZertES, it will certainly be adjustable later.

</details>

**10. POC implementation, what do I have to pay attention to?**

<details><summary>
  Click to see the answer. 
  </summary>

* I have to do a video registration, so I can only sign in the EU.
* This is done here.
* https://trustservices.swisscom.com/en/smart-registration-service/
* I have to register in the Swisscom Shop, so I can then also sign in Switzerland.

</details>

**11. What are the differences between LOA3 and LO4 and why does the downgrade happen?**
<details><summary>
  Click to see the answer. 
  </summary>
 
* LOA3 enables advanced signature

* LOA4 enables a qualified signature

* The reasons for a downgrade from LOA 4 to LOA 3 can be: The identification is older than 5 years, The ID document that was used for identification has expired (the user receives an SMS as a warning 30 days and 90 days beforehand), and The user has changed his means of authentication since the identification

* Change of authentication means means: Change password (link "Forgotten Password"), SIM change, MID reset (without recovery code), MID APP installed and activated (without recovery code), SIM card contract change (without recovery code)
 
</details>

**12. The ETSI checker shows two errors when using static signatures in the generated report in position 5 and 21, why is this the case?**
<details><summary>
  Click to see the answer. 
  </summary>
 
  * ETSI report link, see under PAdES-signature-1, then Full Report. Note: this link works if you are loggedin your ETSI checker account.
https://signatures-conformance-checker.etsi.org/protected/PAdESConf/TestCases/pstoia_ea473cb707cf41e1/localdoc1signed20210421121619timestamp/index.html
 
* The ETSI Signature Conformance Checker does the following (as per their homepage): https://eur03.safelinks.protection.outlook.com/?url=https%3A%2F%2Fsignatures-conformance-checker.etsi.org%2Fpub%2Findex.php&data=04%7C01%7CPaul.Muntean%40swisscom.com%7Cb8b18dbf28584312b2b308d91f7c15a0%7C364e5b87c1c7420d9beec35d19b557a1%7C1%7C0%7C637575440056859327%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=G2QJbPyJOeSZ9Or2M0uZpIF620boeAPf%2FcwLNj85P50%3D&reserved=0

 * The tool performs conformance tests on: XadES, CadES, ASiC, PAdES
 * Verify the conformity of the ETSI Advanced Electronic Signatures
 * It checks the structure of the AdES signature versus the ETSI Specifications

 * When signing the document with a timestamp signature, the resulting document has just a timestamp signature, not an xAdES (Advanced Electronic) signature. Therefore, the checker correctly complains that a timestampped-only document does not conform to the expected signature:

 **Error 5:** 
 * Location-{CodeTest}:SubFilter-{CheckIfValueIsOneOfDefined}
 * Found value: 'ETSI.RFC3161''. Allowed values: adbe.pkcs7.detached,adbe.pkcs7.sha1,ETSI.CAdES.detached
 * This is because the timestamp signature is of type “ETSI.RFC3161”, which is not one of the ones listed above.

 **Error 21:**
 * Location-{CodeTest}:Contents/CAdESSignature-{VerifyCMSOrCAdESWithinPAdES}
 * The CRYPTOGRAPHIC VERIFICATION of the SIGNATURE whose certificate has been issued by "CN=Swisscom TSS CA 4.1,OU=Digital Certificate Services,2.5.4.97=VATAT-U64741248,O=Swisscom IT Services Finance S.E.,C=AT" to "CN=Swisscom TSU 4.1,OU=Digital Certificate Services,O=Swisscom IT Services Finance S.E.,2.5.4.97=VATAT-U64741248,C=AT", and whose serial number is 70191010760937081556668692045972174202, HAS FAILED. Additional details follow: message-digest attribute value does not match calculated value
 
 * This is because the timestampped content is not a CAdES signature content format.

 * So, in conclusion, the timestamping of a document is a particular case of signing a document. The ETSI Checker is not to be used for this specific use case. All the other types of signatures should render all-green reports in the checker.

 
</details>

**13. Can I skip the RA app, Video or similar and benefit from the Fast Track mode?**

<details><summary>
  Click to see the answer. 
  </summary>
 
 * ETSI checker: https://signatures-conformance-checker.etsi.org/pub/index.php
 
 * Business/ Availability: Fast Track Mode (AES)
 * only for +41 numbers/ only for swiss mobile users
 * NO support for non-+41-users within EU
 * no need to get identified via RA APP, Video or similar
 * Technically, how to setup, see below.
 
  * (NA) A.	On request, the signatory receives the document to be signed displayed in full and downloadable before the declaration of intent requesting a signature and after signature, and therefore can be sure that this specific document is signed. This is an obliged requirement!
 
  * (NA) B.	The signatory is informed before or during the expression of will that the signature is an "advanced" signature. This is an obliged requirement!
 
 	* C.	The subscriber acknowledges that a signature can only be executed after acceptance of the terms of use. The terms of use must be shown to the signatory and accepted before the first signing. The signatory must state that it has read, understood and accepted the terms. An opt-in method (e.g. tick box) should be used. Always the latest version of the terms should be shown by use of the following link: https://www.swissdigicert.ch/sdcs/portal/open_pdf?file=english%2FEN_Terms_and_Conditions_CH_pers.pdf 
 
 	* D.	The subscriber application ensures that it has been checked beforehand (e.g. when registering for the account) that the person signing possesses the mobile phone number that will be used later. This can be ensured, for example, by checking the phone number specified by the signer during registration via an SMS service (does not have to be Swisscom SMS service).
 	
* 1.1	Contents of the signature: Signature certificate
* The distinguished name in the signature certificate is as follows:

* cn=<Mobile number of the signatory with prefix "417">

* pseudonym=<Mobile number of the signatory with prefix "417">

* c="CH"

* serialnumber=<current date with format yyyymmdd-<Mobile number of the signatory with prefix "417">>

* a)	You will test the settings at your Test Account (see description below), in addition with the pdfbox examples of Paul
* b)	4.1.3 Own Registration Method with Session Token/OTP only 
* c)	Intentional use: The easiest and fastest way to test the connection to the All-in-signing service. No RA app or Smart Registration Service is used for identification, or you do not want test without identification of the RA app or Smart Registration Service during the test phase and first test the signature connection only. A 1-factor procedure (SMS with one-time password) is used for signature release, which would only be suitable for the use of advanced signatures. Or you plan to use another second factor. 
* d)	Access to the test account jurisdiction CH (ZertES) with the following claimed ID: 
* e)	ais-90days-trial-OTP:OnDemand-Advanced4 
* f)	Access to the test account jurisdiction EU (eIDAS) with the following claimed ID: 
* g)	ais-90days-trial-OTP:OnDemand-Advanced-EU
* h)	we will configure “OTP-only“ for your productive FES Account
 </details>

 **14. I have a serial number mismatch, what can I do to remediate this?**
 <details><summary>
  Click to see the answer. 
  </summary>
  
  * A serial number is related to each customer evidence which we store in our back-end.
  
  * Once the password was changed due to, for example, a password reset, or the MobileID app was reinstaled then a serial number mismatch can appear. This means that the serial number is no longer associated to the customer evidence which we store for that particular customer.
  
  * Remediation: the user has to re-identify himself.
  
  https://srsident.trustservices.swisscom.com/en/
  </details>
 
  **15. When signing I get the user/password iFrame screen, how can I bypass this in order to have a better flow and user experience?**
 <details><summary>
  Click to see the answer. 
  </summary>
  
  * In general we recommend to use MobileID instead of PWD/OTP.
  
  * The password for loggin in case of PWD/OTP can be obtained after confirming the Email the user received with the TCs. The password can at this moment be also reseted.
  
  * You need to activate your MobileID app, this works outside of Switzerland too.
  https://www.mobileid.ch/en
  
  * See also the FAQs under "Mobile ID SIM Card / eSIM"
  https://www.mobileid.ch/en/faq
  
  * After you register with MobileID, accept the TCs (as mentioned above, the user sets his password at this step) and do the SRS video identification you can sign and the user/password screen will be not shown anymore.
  
  </details>
 
  **16. What is a certificate authority (CA), certificate policy (CP), public key infrastructure (PKI), etc.?**
 <details><summary>
  Click to see the answer. 
  </summary>
  
  * A good resource to look this up is here available.
  
  https://pki.goog/faq/#faq-32
  </details>
