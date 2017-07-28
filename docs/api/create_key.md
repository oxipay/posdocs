This endpoint will be used to obtain a device-signing-key using the shared private key. The device-signing-key will then be used to digitally sign all the subsequent messages. See <a href="/security/device_initialisation/">device initialisation</a> for more information.

**Method:** *CreateKey*

<h3>Request</h3>

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
----------|------|-------------
merchantId | Unicode string | Merchant identifier as defined by Oxipay
posDeviceId | Unicode string | Unique device identifier for the POS terminal
clientDeviceId | Unicode string | Oxipay generated globally-unique-device-ID (GUDID) for this terminal
operatorId | Unicode string | ID of POS/terminal operator
firmwareVersion | Unicode string | current firmware version of POS device
company | Unicode string | POS company name
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**
echo <code class="optional">optional</code> | true/false | Determines if Oxipay need to echo back the payload (false by default)
additionalData <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

<h3>Response</h3>

Parameter | Type | Description
----------|------|-------------
status | Unicode string | Success/Failure/Error
code | Unicode string | A code that maps to a <a href="/api_information/status_codes/">specific reason</a>
message | Unicode string | A string explaining the status/code above
key | Hex string | Device-signing-key for the POS terminal. This should be stored securely
requestData | Key-Value pair | If echo was set to <code>true</code> on the request, will contain a flattened key-value pair array of all data sent over the wire
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**

<h3>Testing</h3>

Please contact <a href="mailto:support@oxipay.com.au">support@oxipay.com.au</a> to get access to the test/dummy APIs.

Request -> clientDeviceId | Response -> status | Response -> code
-----------|-----------|-----------
1 | Success | SCRK01
2 | Error | EVAL01
any other value | Error | EISE01

**Testing Assumptions**

* To generate the signature, use a device-signing-key of "1234567890". A invalid signature will cause an ESIG01 Error.
