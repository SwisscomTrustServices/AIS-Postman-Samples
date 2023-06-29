# About
This repository contains several Postman (https://www.postman.com/) samples which can be used when testing the AIS features.

Before starting to use these Postman samples have a look at our AIS reference guide and other references we provide.

Documentation Repository

* https://trustservices.swisscom.com/downloads/

AIS reference Guide

* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf

## Demo Video: Postman Setup

[![Watcht the video](https://i.imgur.com/2qu2MpM.png)](https://youtu.be/D4vIw98qLCU)

## Demo Video: Postman Requests Walkthrough

[![Watch the video](https://i.imgur.com/XyNjPib.png)](https://www.youtube.com/watch?v=mnR3vLCKoGU&list=PL-d189DRx5crNTWYyPhWvCAIWHvCcQVro&index=15)

## Certificate used for AIS trial account

In order to use any of the trial signing requests, you will need to generate a certificate containing identifying information so that the trial customer will accept the requests. Please contact Servicedesk.ICT@swisscom.com for more information.

## RA Samples Description

* https://ras.scapp.swisscom.com/api/evidences/verify
**Verify Request**: This request can be used to check if a user (phoneNumber) is already registered at the RA. Please note, that in the case of reinstalling the MobileID App without using the Backup Code this request response is still successful, but the user is not able to create a qualified signature without a re-identification.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
**Sign Request (static)**: This is the same API call as Sign Request (OnDemand). The difference is that this request will trigger a static signature, for multiple documents, with no 2FA process involved

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
**Sign Request (OnDemand)**: This API call can be used to request a MOBILE ID authentication in order to create a digital signature. The request is asynchronous and will trigger 2FA for the user's number. After the 2FA is confirmed, the Pending request must be used to complete the signing.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/pending
**Singing Service: Pending Request (OnDemand)**: This call is needed to collect the signature status. The status is pending until the user confirms the second factor using the MOBILE ID App. 

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
**Sign Request (OnDemand & Templating)**:  This is the same API call as Sign Request (OnDemand), with the difference that a template is used for the DistinguishedName, providing only variables and allowing AIS to fill the data automatically based on the registered mobile number (msisdn) provided.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/pending
**Pending Request (OnDemand & Templating)**: This call is needed to collect the signature status of the template request shown previously. The status is pending until the user confirms the second factor using the MOBILE ID App. 

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
**Sign Request (OnDemand) Wrong Serial**: This call can be used to test that providing an invalid serial number will prompt AIS to respond with an appropriate error when the pending request is used and 2FA is confirmed.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/pending
**Sign Request (OnDemand) Wrong Serial**: This call is needed to collect the signature status of the invalid serial request shown previously. AIS will respond with an error message instead of a signature, advising the user to identify in RA.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
**Timestamp**: This call can be used to sign a document using only a timestamp, with no 2FA involved.

 ## DSS Postman Sample Videos
 
 How to place a Verify Call using Postman
 
* https://youtu.be/D2-933FV9y4

Signing requests with and without templating using Postman

* https://youtu.be/MXzq_I7YE68

The Postman tool for API endpoint testing explained

* https://youtu.be/jWzvJLHwPhE

How is the Distinguished Name composed and Postman example

* https://youtu.be/vC1_BZO291U

What is a Distinguished Name and for is it usable
* https://youtu.be/rvUythZCKdQ

What is a claimed identity and for what is it usable

* https://youtu.be/L4IQAop-1Ck

How to generate a certificate for digital signing using OpenSSL

* https://youtu.be/bax96Cwnlhg

## Smart-Registration Service Demo Samples

* https://ras-idp-dev.scapp.swisscom.com/oauth/token?client_id=missswaggerclient&client_secret=missswaggerclientsecret&grant_type=client_credentials&scope=miss
SRS flow: This request can be used to retrieve an access_token to be used for the upcoming requests
  
* https://miss-backend-api-preprod.scapp.swisscom.com/api/providers?jurisdiction=EIDAS&loa=3&method=video
SRS flow: This request can be used to retrieve a list of providers for a specific jurisdiction, level of assurance or identification method
  
* https://miss-backend-api-preprod.scapp.swisscom.com/api/providers/test/video
SRS Identification flow: This request can be used to test an identification endpoint (via video) for a specific user. The contents of the request will include information about the user undergoing the identification, such as phone number, first/last name, email and country. The server will respond with a refId that will be used in the next request, as well as details about the identification task.
  
* https://miss-backend-api-preprod.scapp.swisscom.com/api/identifications/{{refId}}
SRS Identification flow: This request can be used to verify the status of the identification task started in the previous request, based on the reference ID (refId). The server responds with information about the task, including the issuer, the identification method, the mobile number and statuses.
  
  For more detailed information on the SRS flow, see section 4 in the Integration guide:
https://documents.swisscom.com/product/filestore/lib/3b44e6a3-3799-4c55-bb6b-8f847c463d31/integration-guide-srs-en.pdf?idxme=pex-search

## ETSI Samples Description

In order to use these Postman samples the user has to first generate a certificate signing request (CSR) and send it to our support team together with the application form. The following formular can be used:
* https://documents.swisscom.com/product/filestore/lib/7668dda8-bd14-4c9c-baaf-fed379adbb72/ordertestaccountauthbroker-en.pdf?idxme=pex-search
  
Next, the user has to configure the certificate which he receives from the support team in Postman or any other used client. Details on how to configure a certificate in Postman can be seen in the first video linked at the top of the readme GitHub repo file.

More details on how to integrate the ETSI interface can be found here.  
* https://trustservices.swisscom.com/hubfs/Website%20Files/Documents/Developer%20Documentation/Reference_Guide_SmartRegistration_Signing-en.pdf?hsLang=de

**Available Postman samples:**

* https://auth.trustservices.swisscom.com/
**Broker Authentication Flow**: In order to generate an auth_code for the /token endpoint, you will need to identify via broker using an appropriate IdP depending on your evidence (MID, PF or PWDOTP). After successful authentication you will receive the code in the URL.

* https://auth.trustservices.swisscom.com/api/auth/realms/broker/protocol/openid-connect/token 
**Broker Token Generation**: This request is used to generate a JWT token for document signing for the upcoming requests by using the code from the previous step and client credentials provided by support after successful trial account onboarding.

* https://ais.swisscom.com/AIS-Server/etsi/standard/rdsc/v1/signatures/signDoc
**ETSI Signing (OnDemand) eIDAS**: This call will sign a document hash using ETSI (OnDemand), eIDAS, and the JWT token generated in the previous step, prompting AIS to respond with the signatureObject after a successful signing.

* https://ais.swisscom.com/AIS-Server/etsi/standard/rdsc/v1/signatures/signDoc
**ETSI Signing (OnDemand) ZertES**: This call will sign a document hash using ETSI (OnDemand), ZertES, and the JWT token generated in the previous step, prompting AIS to respond with the signatureObject after a successful signing.

* https://ais.swisscom.com/AIS-Server/etsi/standard/rdsc/v1/signatures/signDoc
**ETSI Signing (static) eIDAS**: This call will sign a document hash using ETSI (static seal), eIDAS, and the JWT token generated in the previous step, prompting AIS to respond with the signatureObject after a successful signing.

* https://ais.swisscom.com/AIS-Server/etsi/standard/rdsc/v1/signatures/signDoc
**ETSI Signing (static) ZertES**: This call will sign a document hash using ETSI (static seal), ZertES and the JWT token generated in the previous step, prompting AIS to respond with the signatureObject after a successful signing.
 
 ## ETSI Postman Sample Videos
 
 Signing based on the ETSI interface and ZertES.
 
* todo
  
