For Testing the "SendReceipt" API possible response, here list of the parameters on Request. and the backend server will response accordingly

**Assumptions:**

1. All "SendReceipt" API Request's required parameters has been populated.

2. HMAC has been generated on the payload and been put on the signature 

3. invaild signature will return Failed StatusCode therefore not listed below.

**Method:** *SendReceipt*

**StatusCode OutComes by Request Parameters**
**Notes.**
"####" means any 4 charaters

StatusCode | merchantId | clientDeviceId 
-----------|------------|----------------
Success | M2#### | D2#### 
Failed  | M4#### | D4#### 
Error   | M5#### | D5####
