This endpoint will be used to initiate a request that will send an invite to the customer to Login or Register with Oxipay so that they can get a pre-approval code.

**Method:** *Invite*

**Request:**

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
-----------|------|-------------
merchantId | Unicode string | Merchant identifier as defined by Oxipay
mobile | Unicode string | Customer’s mobile number
purchaseAmount | decimal | Total purchase amount
deviceId | Unicode string | Unique device identifier for the POS terminal
operatorId | Unicode string | ID of POS/terminal operator
firmwareVersion | Unicode string | current firmware version of POS device
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key
echo <code class="optional">optional</code> | true/false | Determines if Oxipay need to echo back the payload (false by default)
additional <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

**Response:**

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Success/Failure/Error
message | Unicode string | A string explaining the status above. 
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key
