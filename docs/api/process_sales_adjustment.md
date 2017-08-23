This endpoint will be used to process a Sales Adjustment at the point-of-sale. see <a href="/process/sales_adjustment/">sales adjustment process</a> for more information.

**Method:** *ProcessSalesAdjustment*

<h3>Request</h3>

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
-----------|------|-------------
x_pos_transaction_ref | Unicode string | This is the transaction reference that was passed through as part of the *ProcessAuthorisation* request (or the *SendReceipt* request), which is stored by Oxipay so that it can reconcile sales adjustment requests.
x_merchant_id | Unicode string | Merchant identifier as defined by Oxipay
x_amount | int | Requested adjustment amount (in cents)
x_retry | bool | Flag indicating whether or not this sales adjustment request is a retry for a previous sales adjustment (for the same x_pos_transaction_ref). This is useful if a network failure or other error occurred, whereby the response from the previous sales adjustment request was not received. If the previous sales adjustment was processed then the result from the previous request will be returned. If the previous sales adjustment was not processed, then a new adjustment will be processed and the result returned. There is no limit on the number of retry attempts, but note that a retry is always on the most recent sales adjustment request for the same x_pos_transaction_ref (e.g. if 2 sales adjustments have already been processed, then a 3rd sales adjustment request with the x_retry set true will return the result of the 2nd adjustment)
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
x_message | Unicode string | A string explaining the status/code above. Example: For an Error: Reason why the adjustment cannot be done
tracking_data | Associative array | Echoes tracking_data sent on the request
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

<h3>Testing</h3>

The following describes dummy API requests that return a predictable response. Please contact <a href="mailto:support@oxipay.com.au">support@oxipay.com.au</a> to get access to the test/dummy APIs.

Request -> x_amount | Response -> x_status | Response -> x_code
-----------|-----------|-----------
##01 | Success | SPSA01
##10 | Failed | FPSA01
##11 | Failed | FPSA02
##12 | Failed | FPSA03
##13 | Failed | FPSA04
##14 | Failed | FPSA05
##15 | Failed | FPSA06
##30 | Error | EVAL01
##31 | Error | EAUT01
any other value | Error | EISE01

<span style="color:grey;"><b>#</b> signifies a numeric digit</span>

**Testing Assumptions**

* To generate the signature, use a device-signing-key of "1234567890". A invalid signature will cause an ESIG01 Error.
