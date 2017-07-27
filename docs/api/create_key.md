This endpoint will be used to create a device specific key using the shared private key, that will then be used to digitally sign all the subsequent messages. This will invalidate any existing keys for this device/merchant combination.

**Method:** *CreateKey*

<h3>Request</h3>

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


<h3>Response</h3>

Parameter | Type | Description
----------|------|-------------
statusCode | Unicode string | Codes related to Success/Failure/Error
message | Unicode string | A string explaining the status above
key | Hex string | Private key for the POS terminal
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a **shared private key**

<h3>Testing</h3>

Using the test WSDL <code>https://testpos.oxipay.com.au:53821/Service/svc?wsdl</code>; use the following request parameters to generate a predictable response:

Request -> clientDeviceId | Response -> StatusCode
-----------|----------------
1 | Success
2 | Failed
3 | Error

**Testing Assumptions**

1. All required fields must be populated. Missing required fields will result in an "Error" StatusCode being returned.
2. Fields will still be validated. An invalid field will result in an "Error" StatusCode being returned.
3. To generate the signature, use a device-signing-key of "1234567890".
4. An invaild signature will return a "Failed" StatusCode.
5. Any request paramter combination not explicitly listed above will result in an "Error" StatusCode being returned.
