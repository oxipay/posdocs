For Testing the "ProcessAuthorisation" API possible response, here list of the parameters on Request. and the backend server will response accordingly

**Assumptions:**

1. All "ProcessAuthorisation" API Request's required parameters has been populated.

2. HMAC has been generated on the payload and been put on the signature 

3. Invaild signature will return Failed StatusCode therefore not listed below.

4. Any request paramters combindation that not listed below will return Error Status

**Method:** *ProcessAuthorisation*

**StatusCode OutComes by Request Parameters**
**Notes.**
"preApprovalCode" is 8 digit, if length not match, go to Failed Status.

StatusCode | preApprovalCode 
-----------|------------------
Approved | 12345678
Declined | 98765432 
Error    | 55555555