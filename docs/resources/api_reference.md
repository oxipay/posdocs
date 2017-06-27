This sections details the various Oxipay APIs that can be used by POS to process in-store transactions.

## Device Setup

These set of endpoints will enable POS to create/reset private keys that will be used to digitally sign the messages between POS and Oxipay.

### Create Key

This endpoint will be used to create a device specific key using the shared private key, that will then be used to digitally sign all the subsequent messages. This will invalidate any existing keys for this device/merchant combination.

**Method:** *CreateKey*

**Request:**

Parameter | Type | Description
-----------|------|-------------
merchantId | Unicode string | Merchant identifier as defined by Oxipay
deviceId | Unicode string | Unique device identifier for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**

**Response:**

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Success/Failure/Error
message | Unicode string | A string explaining the status above
key | Hex string | Private key for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**


### Process Authorisation

This endpoint will process an authorisation to finalise the transaction

**Method:** *ProcessAuthorisation*

**Request:**

Parameter | Type | Description
-----------|------|-------------
posTransactionRef | Unicode string | A transaction reference from POS
merchantId | Unicode string | Merchant identifier as defined by Oxipay
purchaseAmount | decimal | Total purchase amount
financeAmount | decimal | Amount that the customer wants the finance for from Oxipay
preApprovalCode | Unicode string | The pre-approval code obtained from barcode that the customer presented
deviceId | Unicode string | Unique device identifier for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

**Response:**

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Approved/Declined/Error
message | Unicode string | A string explaining the status above. Example: For an Approval, what will be customer’s first direct debit date. For an Error: Bank declined – Insufficient Funds 
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key 


### Invite

This endpoint will be used to initiate a request that will send an invite to the customer to Login or Register with Oxipay so that they can get a pre-approval code.

**Method:** *Invite*

**Request:**

Parameter | Type | Description
-----------|------|-------------
merchantId | Unicode string | Merchant identifier as defined by Oxipay
mobile | Unicode string | Customer’s mobile number
purchaseAmount | decimal | Total purchase amount
deviceId | Unicode string | Unique device identifier for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

**Response:**

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Success/Failure/Error
message | Unicode string | A string explaining the status above. 
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key 


### Sales Adjustment/Refund

This endpoint will be used to process a Sales Adjustment at the point-of-sale.

**Method:** *ProcessAdjustment*

**Request:**

Parameter | Type | Description
-----------|------|-------------
posTransactionRef | Unicode string | A transaction reference from POS
merchantId | Unicode string | Merchant identifier as defined by Oxipay
amount | decimal | Requested adjustment amount
adjustmentCode | Unicode string | Requested amount for adjustment
deviceId | Unicode string | Unique device identifier for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

**Response:**

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Approved/Declined/Error
message | Unicode string | A string explaining the status above. Example: For an Error: Reason why the adjustment cannot be done
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key 
