Your POS integration for Oxipay will need to support 2 experiences.

* [Merchant Initiated Flow](process/merchant_initiated_flow.md)
* [Customer initiated flow](process/customer_initiated_flow.md)

In order to implement these flows you will need to do the following and we suggest starting with the Merchant Initiated Flow: 


## Setup 
1. Login to the Merchant Area using your Merchant Id and Password: 
   https://uatportals.oxipay.com.au/#/login 
   (Click on the Merchant Login link)
2. *Initialise the POS device*
   You will need to generate a POS Device Token from the Merchant Area.

## Merchant initiated flow


1. Capture the customers Mobile Phone number.
2. POS device initiates invitation request
3. Customer will receive an SMS
4. Customer logs in or registers for an Oxipay account.
5. Customer will get a pre-approval code (presented as a barcode) for a pre-approved amount
6. The process from here is now the same as the customer initiated flow. 


## Customer initiated flow 

1. Create an Oxipay customer account (https://uatportals.oxipay.com.au/#/login)
2. Generate a barcode
3. POS will scan the barcode
4. POS Calls Oxipay and receives a response
5. Confirm with customer



