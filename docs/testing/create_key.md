For Testing the "CreateKey" API possible response, here list of the parameters on Request. and the backend server will response accordingly

**Assumptions:**

1. All "Createkey" API Request's required parameters has been populated.

2. HMAC has been generated on the payload and been put on the signature 

3. Invaild signature will return Failed StatusCode therefore not listed below.

4. Any request paramters combindation that not listed below will return Error Status

**Method:** *CreateKey*

**StatusCode OutComes by Request Parameters**
**Notes.**
"####" means any 4 charaters

StatusCode | merchantId | clientDeviceId 
-----------|------------|----------------
Success | M2#### | D2#### 
Failed  | M4#### | D4#### 
Error   | M5#### | D5####
