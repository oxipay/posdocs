<strong>API reference: <a href="/resources/api_reference/#invite">Invite</a></strong>

In scenarios where the customer does not have a pre-approval code from Oxipay but want to use Oxipay as a finance option, merchants will have the ability to call an Invite API to facilitate the process.

Oxipay expects customer's mobile number in the payload and will use that to send an SMS to customer. It will contain Login (for already registered customers) or Register (for new customers) link.