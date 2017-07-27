This endpoint will process an authorisation to finalise the transaction

**Method:** *ProcessAuthorisation*

**Request:**

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
-----------|------|-------------
posTransactionRef | Unicode string | A transaction reference from POS
merchantId | Unicode string | Merchant identifier as defined by Oxipay
purchaseAmount | decimal | Total purchase amount
financeAmount | decimal | Amount that the customer wants the finance for from Oxipay
preApprovalCode | Unicode string | The pre-approval code obtained from barcode that the customer presented
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
message | Unicode string | A string explaining the status above. Example: For an Approval, what will be customer’s first direct debit date. For an Error: Bank declined – Insufficient Funds 
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key 
