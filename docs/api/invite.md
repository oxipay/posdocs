This endpoint will be used to initiate a request that will send an invite to the customer to Login or Register with Oxipay so that they can get a pre-approval code.

**Method:** *Invite*

<h3>Request</h3>

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
-----------|------|-------------
x_merchant_id | Unicode string | Merchant identifier as defined by Oxipay
x_mobile | Unicode string | Customer’s mobile number
x_purchase_amount | decimal | Total purchase amount
x_device_id | Unicode string | Unique device identifier for the POS terminal
x_operator_id | Unicode string | ID of POS/terminal operator
x_firmware_version | Unicode string | current firmware version of POS device
tracking_data <code class="optional">optional</code> | Associative array | A map that can be populated with additional tracking/state information that will get passed back in the response
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

<h3>Response</h3>

Parameter | Type | Description
-----------|------|-------------
x_status | Unicode string | Success/Failure/Error
x_code | Unicode string | A code that maps to a <a href="/api_information/status_codes/">specific reason</a>
x_message | Unicode string | A string explaining the status/code above. 
tracking_data | Associative array | Echoes tracking_data sent on the request
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

<h3>Testing</h3>

The following describes dummy API requests that return a predictable response. Please contact <a href="mailto:support@oxipay.com.au">support@oxipay.com.au</a> to get access to the test/dummy APIs.

Request -> x_purchase_amount | Response -> x_status | Response -> x_code
-----------|-----------|-----------
##.01 | Success | SINV01
##.02 | Error | EVAL01
##.03 | Error | EAUT01
any other value | Error | EISE01

<span style="color:grey;"><b>#</b> signifies a numeric digit</span>

**Testing Assumptions**

* To generate the signature, use a device-signing-key of "1234567890". A invalid signature will cause an ESIG01 Error.
