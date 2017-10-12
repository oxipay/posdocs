<h3>Retries &amp; Idempotency</h3>

<b>Process Authorisation</b>

On calls to the ProcessAuthorisation API, the pre-approval code (as specified by the x_pre_approval_code parameter) is flagged as 'used'. Once used, a pre-approval code can never again be reused to get consumer finance. If an already used pre-approval code is passed through on a seperate call to ProcessAuthorisation (with a different digital-signature to the inital call), a status code of 'FPRA22' (see <a href="/api_information/status_codes/">status codes</a>) will be returned - the Barcode has already been used.

There is one exception to the above; In a timeout scenario (e.g. where the bank takes longer than expected to process the initial payment), the same pre-approval can be passed through in a subsequent retry attempt - as long as the request is exactly the same, that is, with a digital-signature that matches the initial call. In this scenario, the ProcessAuthorisation API will instead return the current authorisation status. It is therefore safe to call the ProcessAuthorisation API using the same pre-approval code (and same message with the same digital-signature) until a status is returned.

<b>Send Receipt</b>

The SendReceipt API simply associates a POS transaction reference to the authorisation. An authorisation can have zero-to-many POS transaction references, which means that this API can be called as many times as needed to associate more POS transaction references to the authorisation.

<b>Process Sales Adjustment</b>

Similar to the ProcessAuthorisation API, there are certain scenarios, such as timeouts and network failures, where we might need to 'retry' a single sales adjustment attempt. However, unlike the ProcessAuthorisation API, it is actually valid to call this API multiple times e.g. multiple partial refunds for individual line-items. For this reason, every sales adjustment must specify a unique transaction reference for the adjustment, x_pos_transaction_ref, in addition to the original purchase reference, x_pos_purchase_ref. The x_pos_transaction_ref field allows Oxipay to determine if this is a retry on a single sales adjustment attempt, or if it's a new sales adjustment attempt.
