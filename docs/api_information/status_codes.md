<h3>Statuses and codes</h3>

There are 3 unique statuses as follows:

* **Success**: When the intent of the request is successful e.g. an Approval from the *ProcessAuthorisation* API.
* **Failed**: When the intent of the request is unsuccessful e.g. a Decline from the *ProcessAuthorisation* API.
* **Error**: When there is a problem with the request or an unexpected error.

The following table defines statuses, codes, and messages returned by the Oxipay APIs. The reason for the unique codes is to make life a bit easier for integrators that want to display their own custom messages.

Status | Code | API | Message
----------|----------|----------|----------
Success | SCRK01 | CreateKey | Success
Success | SINV01 | Invite | Success
Success | SPRA01 | ProcessAuthorisation | Approved
Success | SPSA01 | ProcessSalesAdjustment | Approved
Success | SSER01 | SendReceipt | Success
Failed | FPRA01 | ProcessAuthorisation | Declined due to internal risk assessment against the customer
Failed | FPRA02 | ProcessAuthorisation | Declined due to insufficient funds for the deposit
Failed | FPRA03 | ProcessAuthorisation | Declined as communication to the bank is currently unavailable
Failed | FPRA04 | ProcessAuthorisation | Declined because the customer limit has been exceeded
Failed | FPRA05 | ProcessAuthorisation | Declined due to negative payment history for the customer
Failed | FPRA06 | ProcessAuthorisation | Declined because the credit-card used for the deposit is expired
Failed | FPRA07 | ProcessAuthorisation | Declined because supplied posTransactionRef has already been processed
Failed | FPSA01 | ProcessSalesAdjustment | Unable to find the specified POS transaction reference
Failed | FPSA02 | ProcessSalesAdjustment | This contract has already been completed
Failed | FPSA03 | ProcessSalesAdjustment | This Oxipay contract has previously been cancelled and all payments collected have been refunded to the customer
Failed | FPSA04 | ProcessSalesAdjustment | Sales adjustment cannot be processed for this amount
Failed | FPSA05 | ProcessSalesAdjustment | Unable to process a sales adjustment for this contract. Please contact Merchant Services on 1300 413 902 during business hours for further information
Failed | FSER01 | SendReceipt | Unable to find the specified POS transaction reference
Failed | FSER02 | SendReceipt | The specified POS transaction reference is already in use
Failed | FCRK01 | CreateKey | Unable to find the specified client device id
Error | EVAL01 | * | Validation error
Error | EAUT01 | * | Authentication error
Error | ESIG01 | * | Signature mismatch error
Error | EISE01 | * | Internal server error
