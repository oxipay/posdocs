This endpoint will process an authorisation to finalise the transaction

**Method:** *ProcessAuthorisation*

<h3>Request</h3>

Parameter &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;| Type | Description
-----------|------|-------------
x_pos_transaction_ref | Unicode string | This must be the same reference that would get passed through on future *ProcessSalesAdjustment* requests. This field is mandatory - if the POS system does not have this information at the time of the request, it should pass through a temporary unique value (e.g. a GUID) so that Oxipay has the information it needs to process retry attempts. If a temporary value *is* used; a subsequent request to *SendReceipt* **must** be made when the actual transaction reference is known by the POS system, so that Oxipay can successfully reconcile future *ProcessSalesAdjustment* requests.
x_merchant_id | Unicode string | Merchant identifier as defined by Oxipay
x_purchase_amount | int | Total purchase amount (in cents)
x_finance_amount | int | Amount that the customer wants the finance for from Oxipay (in cents)
x_pre_approval_code | Unicode string | The pre-approval code obtained from barcode that the customer is presented
purchase_items | String array | A string array with the description of items purchased
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
x_message | Unicode string | A string explaining the status/code above. Example: For an Approval, what will be customer’s first direct debit date. For an Error: Bank declined – Insufficient Funds
tracking_data | Associative array | Echoes tracking_data sent on the request
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key

<h3>Testing</h3>

The following describes dummy API requests that return a predictable response. Please contact <a href="mailto:support@oxipay.com.au">support@oxipay.com.au</a> to get access to the test/dummy APIs.

Request -> x_pre_approval_code | Response -> x_status | Response -> x_code
-----------|-----------|-----------
01###### | Success | SPRA01
10###### | Failed | FPRA01
11###### | Failed | FPRA02
12###### | Failed | FPRA03
13###### | Failed | FPRA04
14###### | Failed | FPRA05
15###### | Failed | FPRA06
16###### | Failed | FPRA07
17###### | Failed | FPRA08
18###### | Failed | FPRA21
19###### | Failed | FPRA22
20###### | Failed | FPRA23
21###### | Failed | FPRA24
22###### | Failed | FPRA99
23###### | Failed | FPRA09
30###### | Error | EVAL01
31###### | Error | EAUT01
any other value | Error | EISE01

<span style="color:grey;"><b>#</b> signifies an alphanumeric digit</span>

**Testing Assumptions**

* To generate the signature, use a device-signing-key of "1234567890". A invalid signature will cause an ESIG01 Error.
