<h3>Statuses and codes</h3>

Status | Code | API | Message
----------|----------|----------|----------
Success | SCRK01 | CreateKey | Success
Success | SINV01 | Invite | Success
Success | SPRA01 | ProcessAuthorisation | Approved
Success | SPSA01 | ProcessSalesAdjustment | Approved
Success | SSER01 | SendReceipt | Success
Failed | FPRA01 | ProcessAuthorisation | Declined due to internal risk assessment against the buyer
Failed | FPRA02 | ProcessAuthorisation | Declined due to insufficient funds for the deposit
Failed | FPRA03 | ProcessAuthorisation | Declined as communication to the bank is currently unavailable
Failed | FPRA04 | ProcessAuthorisation | Declined because the buyer limit has been exceeded
Failed | FPRA05 | ProcessAuthorisation | Declined due to negative payment history for the buyer
Failed | FPRA05 | ProcessAuthorisation | Declined because the credit-card used for the depoit is expired
Failed | FPRA06 | ProcessAuthorisation | Declined because supplied posTransactionRef has already been processed
Failed | FPSA01 | ProcessSalesAdjustment | Unable to find the specified POS transaction reference
Failed | FPSA02 | ProcessSalesAdjustment | This contract has already been completed
Failed | FPSA03 | ProcessSalesAdjustment | This Oxipay contract has previously been cancelled and all payments collected have been refunded to the buyer
Failed | FPSA04 | ProcessSalesAdjustment | Sales adjustment cannot be processed for this amount
Failed | FPSA05 | ProcessSalesAdjustment | Unable to process a sales adjustment for this contract. Please contact Merchant Services on 1300 413 902 during business hours for further information
Error | EVAL01 | * | Validation error
Error | ESIG01 | * | Signature mismatch error
Error | EISE01 | * | Internal server error
