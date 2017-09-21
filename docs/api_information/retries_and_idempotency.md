<h3>Retries &amp; Idempotency</h3>

<b>Process Authorisation</b>

The very first thing that's done on calls to the ProcessAuthorisation API, is that the pre-approval code (as specified by the x_pre_approval_code parameter) is flagged as 'used'. Once used, a pre-approval code can never again be reused to get consumer finance. If an already used pre-approval code is passed through on a call to ProcessAuthorisation, it will not be re-processed - the current authorisation status will instead be returned.

A use-case where the above scenario is relevant, is the timeout scenario. If, for example, the bank takes longer than expected to process the deposit a ProcessAuthorisation timeout might occur at the point of sale. In this scenario, it is safe to call the ProcessAuthorisation API using the same pre-approval code until a status is returned.

<b>Send Receipt</b>

The SendReceipt API simply associates a POS transaction reference to the authorisation. An authorisation can have zero-to-many POS transaction references, so basically this API can be called as many times as needed to associate more POS transaction references to the authorisation.

<b>Process Sales Adjustment</b>

Similar to the ProcessAuthorisation API, there are certain scenarios, such as timeouts and network failures, where we might need to do a 'retry' on a single sales adjustment attempt. However, unlike the ProcessAuthorisation API, it is actually valid to call this API multiple times e.g. multiple partial refunds for individual line-items. For this reason, we need an additional parameter, x_retry, to specify, whether or not, this is a retry on a single sales adjustment attempt, or if it's a new sales adjustment attempt.
