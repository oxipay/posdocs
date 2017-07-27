This endpoint will be used to create a device specific key using the shared private key, that will then be used to digitally sign all the subsequent messages. This will invalidate any existing keys for this device/merchant combination.

**Method:** *CreateKey*

**Request:**

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
----------|------|-------------
merchantId | Unicode string | Merchant identifier as defined by Oxipay
posDeviceId | Unicode string | Unique device identifier for the POS terminal
clientDeviceId | Unicode string | Oxipay generated device ID for this terminal (this is globally unique)
operatorId | Unicode string | ID of POS/terminal operator
firmwareVersion | Unicode string | current firmware version of POS device
company | Unicode string | POS company name
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**
echo <code class="optional">optional</code> | true/false | Determines if Oxipay need to echo back the payload (false by default)
additional <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information


**Response:**

Parameter | Type | Description
----------|------|-------------
statusCode | Unicode string | Codes related to Success/Failure/Error
message | Unicode string | A string explaining the status above
key | Hex string | Private key for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**
