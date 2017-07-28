This endpoint will process an authorisation to finalise the transaction

**Method:** *ProcessAuthorisation*

<h3>Request</h3>

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
additionalData <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

<h3>Response</h3>

Parameter | Type | Description
-----------|------|-------------
status | Unicode string | Success/Failure/Error
code | Unicode string | A code that maps to a <a href="/api_information/status_codes/">specific reason</a>
message | Unicode string | A string explaining the status/code above. Example: For an Approval, what will be customer’s first direct debit date. For an Error: Bank declined – Insufficient Funds 
requestData | Key-Value pair | If echo was set to <code>true</code> on the request, will contain a flattened key-value pair array of all data sent over the wire
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key 

<h3>Testing</h3>

Please contact <a href="mailto:support@oxipay.com.au">support@oxipay.com.au</a> to get access to the test/dummy APIs.

Request -> preApprovalCode | Response -> status | Response -> code
-----------|-----------|-----------
######01 | Success | SPRA01
######01 | Failed | FPRA01
######02 | Failed | FPRA02
######03 | Failed | FPRA03
######04 | Failed | FPRA04
######05 | Failed | FPRA05
######06 | Failed | FPRA06
######07 | Failed | FPRA07
######10 | Error | EVAL01
######11 | Error | ESIG01
######12 | Error | EISE01

<span style="color:grey;"><b>#</b> signifies an alphanumeric digit</span>

**Testing Assumptions**

* All required fields must be populated and all fields will still be validated. Missing required fields or invalid data will result in an validation error
* To generate the signature, use a device-signing-key of "1234567890"
* Any request parameter combination not explicitly listed above will result in an internal server error
