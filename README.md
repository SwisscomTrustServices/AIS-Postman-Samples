# About
This repository contains several Postman samples which can be used when testng AIS features.

Before starting to use these Postman Samples have a look at our AIS refence guide.
https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf

Demo Video about using the samples in Postman.
https://onedrive.live.com/?authkey=%21AOOgsr9maiK5feg&cid=2D4A6425D2D29B86&id=2D4A6425D2D29B86%21668&parId=2D4A6425D2D29B86%21662&o=OneUp
or


# Samples Descriptions

* https://ras.scapp.swisscom.com/api/evidences/verify
RA Service Lookup: This request can be used to check if a user (phoneNumber) is already registered at the RA. Please note, that in the case of reinstalling the MobileID App without using the Backup Code this request response is still successful but the user is not able to create a qualified signature without a reidentification.

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
RA Service Sign Request (OnDemand): This API call can be used to request a MOBILE ID authentication in order to create a digital signature. 

* https://ais.swisscom.com/AIS-Server/rs/v1.0/sign
RA Service Sign Request (OnDemand) Batch: This is the same API call as RA Service Sign Request (OnDemand). The difference is that it is possible to request more than one signature. Please note that the request body format is not a valid JSON and needs to be prepared as a string. 

* https://ais.swisscom.com/AIS-Server/rs/v1.0/pending
Singing Service: Pending Request (OnDemand): This call is needed to collect the signature status. The status is pending until the user confirms the second factor using the MOBILE ID App. 

