# About
This repository contains several Postman (https://www.postman.com/) samples which can be used when testing the AIS features.

Before starting to use these Postman samples have a look at our AIS reference guide and other references we provide.

Documentation Repository

* https://trustservices.swisscom.com/downloads/

AIS reference Guide

* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf

## Demo Video: Postman Samples
* https://onedrive.live.com/?authkey=%21AOOgsr9maiK5feg&cid=2D4A6425D2D29B86&id=2D4A6425D2D29B86%21668&parId=2D4A6425D2D29B86%21662&o=OneUp

or alternatively if you cannot access the first link, you need to download the raw video file using the following link.

* https://github.com/SwisscomTrustServices/AIS-Postman-Samples/blob/main/20201201_PostmanSetup_mTLS-configuration.mp4


## RA Samples Description

* https://ras.scapp.swisscom.com/api/evidences/verify
RA Service Lookup: This request can be used to check if a user (phoneNumber) is already registered at the RA. Please note, that in the case of reinstalling the MobileID App without using the Backup Code this request response is still successful, but the user is not able to create a qualified signature without a re-identification.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
RA Service Sign Request (OnDemand): This API call can be used to request a MOBILE ID authentication in order to create a digital signature. 

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
RA Service Sign Request (OnDemand) Batch: This is the same API call as RA Service Sign Request (OnDemand). The difference is that it is possible to request more than one signature. Please note that the request body format is not a valid JSON and needs to be prepared as a string. 

* https://ais.swisscom.com/AIS-Server/rs/v1.0/pending
Singing Service: Pending Request (OnDemand): This call is needed to collect the signature status. The status is pending until the user confirms the second factor using the MOBILE ID App. 

## iText7 Demo Samples Description

To be able to run the following requests, you need to configure and run locally the 
[iText7 AIS Demo app](https://github.com/SwisscomTrustServices/itext7-ais-demo).

* http://localhost:8080/ais/on-demand-step-up-file?inputFilePath={{input_file_path}}&outputFilePath={{output_file_path}}
On Demand Advanced with Stepup (MID/PWD/OTP) flow: This request can be used to sign a PDF identified by the file path on the local machine and to 
  write the signed document on the provided output file path. As a response, the status message of the operation will be returned.
  
* http://localhost:8080/ais/static-multipart
Static (multipart file) flow: This request can be used to sign a form-data PDF. As a response, the signed PDF encoded into ``base 64`` 
  will be returned.
  
* http://localhost:8080/ais/timestamp-batch
Timestamp (batch files) flow: This request can be used to sign multiple form-data PDFs in a batch. As a response, the signed PDF encoded into 
  ``base 64`` will be returned.
  
* http://localhost:8080/ais/dynamic?inputFilePath={{input_file_path}}&outputFilePath={{output_file_path}}&signatureMode={{signature_mode}}
Dynamic file: This request can be used to sign a PDF identified by the file path on the local machine and to write the signed document on the 
  provided output file path. It uses the flow specified by the `signatureMode` query param. The possible values are: `ON_DEMAND_WITH_STEP_UP`, 
  `ON_DEMAND` (with RA service), `STATIC` and `TIMESTAMP`. As a response, the status message of the operation will be returned.