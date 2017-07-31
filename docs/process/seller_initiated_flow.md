<strong>API references: </strong>

 - <a href="/api/process_authorisation/">ProcessAuthorisation</a>
 - <a href="/api/invite/">Invite</a>

The seller-initiated flow occurs when a buyer arrives at the point-of-sale without a pre-approval code. Ideally, the buyer would already have a pre-approval code as the buyer-initiated flow is much more streamlined and synchronous*. Every effort should be made by ratailers to funnel buyers to the <a href="/process/buyer_initiated_flow/">buyer-initiated</a> flow. These efforts might include the following:

* Oxipay tags on products that can be read by mobile devices (e.g. QR code) that take buyers to the registration screen.
* Sales people driving buyers to register before getting to the point of sale.

The seller-initiated flow is a two step process. The first part involves the POS system brokering an Oxipay invite to the buyer (by sending an SMS with a link to the registration screen). Once the buyer has registered, the rest of the process is same as buyer-initiated flow.

<div style="color: grey;">* by <b>synchronous</b> we mean the buyer and seller are on the same workflow. The seller-initiated flow is <b>asynchronous</b> whereby the buyer might be completing registration at the same time the seller is tending to other POS transactions.</div><br/>


<strong>Step 1</strong>
<img src="/img/flows/cust-init-1.png" alt="Oxipay Merchant Initiated Flow">

---

<strong>Step 2</strong>

<p style="text-align: center;"><img src="/img/flows/cust-init-2.png" alt="Oxipay Buyer Initiated Flow"></p>
