This endpoint will be used to process a Sales Adjustment at the point-of-sale. see <a href="/process/sales_adjustment/">sales adjustment process</a> for more information.

**Method:** *ProcessSalesAdjustment*

<h3>Request</h3>

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
additionalData <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

<h3>Response</h3>

Parameter | Type | Description
-----------|------|-------------
status | Unicode string | Success/Failure/Error
code | Unicode string | A code that maps to a <a href="/api_information/status_codes/">specific reason</a>
message | Unicode string | A string explaining the status/code above. Example: For an Error: Reason why the adjustment cannot be done
requestData | Key-Value pair | If echo was set to <code>true</code> on the request, will contain a flattened key-value pair array of all data sent over the wire
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

<h3>Testing</h3>

Please contact <a href="mailto:support@oxipay.com.au">support@oxipay.com.au</a> to get access to the test/dummy APIs.

Request -> amount | Response -> status | Response -> code
-----------|-----------|-----------
##.01 | Success | SPSA01
##.02 | Failed | FPSA01
##.03 | Failed | FPSA02
##.04 | Failed | FPSA03
##.05 | Failed | FPSA04
##.06 | Failed | FPSA05
##.10 | Error | EVAL01
any other value | Error | EISE01

<span style="color:grey;"><b>#</b> signifies a numeric digit</span>

**Testing Assumptions**

* To generate the signature, use a device-signing-key of "1234567890". A invalid signature will cause an ESIG01 Error.
