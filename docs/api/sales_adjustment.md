This endpoint will be used to process a Sales Adjustment at the point-of-sale.

**Method:** *ProcessAdjustment*

**Request:**

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
-----------|------|-------------
posTransactionRef | Unicode string | A transaction reference from POS
merchantId | Unicode string | Merchant identifier as defined by Oxipay
amount | decimal | Requested adjustment amount
receipt | Unicode string | POS's receipt number for the original transaction
deviceId | Unicode string | Unique device identifier for the POS terminal
operatorId | Unicode string | ID of POS/terminal operator
firmwareVersion | Unicode string | current firmware version of POS device
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key
echo <code class="optional">optional</code> | true/false | Determines if Oxipay need to echo back the payload (false by default)
additional <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

**Response:**

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Approved/Declined/Error
message | Unicode string | A string explaining the status above. Example: For an Error: Reason why the adjustment cannot be done
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key
