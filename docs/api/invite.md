This endpoint will be used to initiate a request that will send an invite to the customer to Login or Register with Oxipay so that they can get a pre-approval code.

**Method:** *Invite*

<h3>Request</h3>

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
additionalData <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

<h3>Response</h3>

Parameter | Type | Description
-----------|------|-------------
status | Unicode string | Success/Failure/Error
code | Unicode string | A code that maps to a <a href="/api_information/status_codes/">specific reason</a>
message | Unicode string | A string explaining the status/code above. 
requestData | Key-Value pair | If echo was set to <code>true</code> on the request, will contain a flattened key-value pair array of all data sent over the wire
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

<h3>Testing</h3>

Request -> purchaseAmount | Response -> status | Response -> code
-----------|-----------|-----------
##.#1 | Success | SINV01
##.#2 | Error | EVAL01
##.#3 | Error | ESIG01
##.#4 | Error | EISE01

<span style="color:grey;"><b>#</b> signifies a numeric digit</span>

**Testing Assumptions**

* All required fields must be populated and all fields will still be validated. Missing required fields or invalid data will result in an validation error
* To generate the signature, use a device-signing-key of "1234567890"
* Any request paramter combination not explicitly listed above will result in an internal server error
