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
additional <code class="optional">optional</code> | Key-Value pair | A map that can be populated with additional information

<h3>Response</h3>

Parameter | Type | Description
-----------|------|-------------
statusCode | Unicode string | Codes related to Approved/Declined/Error
message | Unicode string | A string explaining the status above. Example: For an Approval, what will be customer’s first direct debit date. For an Error: Bank declined – Insufficient Funds 
signature | Hex string case-insensitive | Payload that is signed using HMAC-SHA256 using a device specific key 

<h3>Testing</h3>

Using the test WSDL <code>https://testpos.oxipay.com.au:53821/Service/svc?wsdl</code>; use the following request parameters to generate a predictable response:

Request -> preApprovalCode | Response -> StatusCode
-----------|------------
#######1 | Approved
#######2 | Declined
#######3 | Error

<span style="color:grey;"><b>#</b> signifies a alphanumeric digit</span>

**Testing Assumptions**

1. All required fields must be populated. Missing required fields will result in an "Error" StatusCode being returned.
2. Fields will still be validated. An invalid field will result in an "Error" StatusCode being returned.
3. To generate the signature, use a device-signing-key of "1234567890".
4. An invaild signature will return a "Failed" StatusCode.
5. Any request paramter combination not explicitly listed above will result in an "Error" StatusCode being returned.
