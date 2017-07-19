## Device Initialisation / Setup

<strong>API reference: <a href="/resources/api_reference/#create-key">CreateKey</a></strong>

Every POS device will have its own device specific key that it needs to use to create a digital signature for all the messages when communicating with Oxipay. This device key will be generated on the fly during the device initialisation process.

POS will need to know the following Merchant specific information to carry out the device setup process:

- **Merchant ID** (provided to merchant by Oxipay as part of merchant onboarding)
- **Merchant API Key** (this is the shared private key - provided to merchant by Oxipay as part of merchant onboarding)


Device initialisation/setup is a process of setting up the initial (once off) handshaking between POS and Oxipay. It involves the POS calling <a href="/resources/api_reference/#Create Key">CreateKey</a> API and use the Merchant API Key to digitally sign the payload. Oxipay will then return a Device Key that will need to be stored in POS and will be used for signing all subsequent messages from that POS device.