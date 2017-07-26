For Testing the "ProcessAdjustment" API possible response, here list of the parameters on Request. and the backend server will response accordingly

**Assumptions:**

1. All "ProcessAdjustment" API Request's required parameters has been populated.

2. HMAC has been generated on the payload and been put on the signature 

3. Invaild signature will return Failed StatusCode therefore not listed below.

4. Any request paramters combindation that not listed below will return Error Status

**Method:** *ProcessAdjustment*

**StatusCode OutComes by Request Parameters**
**Notes.**
"####" means any 4 charaters

StatusCode | merchantId | clientDeviceId | amount 
-----------|------------|----------------|--------
Approved  | M2#### | D2#### | >0
Declined   | M4#### | D4#### | <= 0
Error   | M5#### | D5#### | any