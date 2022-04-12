# About
This repository contains several Postman (https://www.postman.com/) samples which can be used when testing the AIS features.

Before starting to use these Postman samples have a look at our AIS reference guide and other references we provide.

Documentation Repository

* https://trustservices.swisscom.com/downloads/

AIS reference Guide

* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf

## Demo Video: Postman Samples

[![Watcht the video](https://i.imgur.com/2qu2MpM.png)](https://youtu.be/D4vIw98qLCU)

or see it in OneDrive:

* https://onedrive.live.com/?authkey=%21AOOgsr9maiK5feg&cid=2D4A6425D2D29B86&id=2D4A6425D2D29B86%21668&parId=2D4A6425D2D29B86%21662&o=OneUp


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
 
 ## Additional Postman Sample Videos
 
* https://youtu.be/D2-933FV9y4

How to place a Verify Call using Postman

* https://youtu.be/MXzq_I7YE68

Signing requests with and without templating using Postman

* https://youtu.be/jWzvJLHwPhE

The Postman tool for API endpoint testing explained

* https://youtu.be/vC1_BZO291U

How is the Distinguished Name composed and Postman example

* https://youtu.be/rvUythZCKdQ

What is a Distinguished Name and for is it usable

* https://youtu.be/L4IQAop-1Ck

What is a claimed identity and for what is it usable

* https://youtu.be/bax96Cwnlhg

How to generate a certificate for digital signing using OpenSSL
