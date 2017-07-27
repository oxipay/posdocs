<h1>Device Initialisation</h1>

All API requests and responses are signed using <a href="https://en.wikipedia.org/wiki/Hash-based_message_authentication_code">HMAC-SHA256</a>. The message authentication code (MAC) is hashed using SHA256 and a secret cryptographic key. Each individual device (e.g. a POS terminal) has its own secret cryptographic key with which to generate digital signatures. No other device will be able to produce a matching HMAC unless it also knows the original devices secret key. These device specific cryptographic keys are known as 'device-signing-keys'.

It is extremely important to restrict access to the device-signing-keys. Once someone has this information (as well as few other details such as the MAC algorithm, hash algorith, and the production endpoint locations) they ***would*** be able to circumvent the signing mechanism. One potential (mis)use of this information could result in someone processing their own sales adjustments thereby defrauding the merchant.

Due to the importance of keeping the device-signing-keys out of the wrong hands. A device initialisation process was devised to keep device-signing-keys out of hands altogether! Nobody, not even the technitions who configure the POS terminals, would have access to the device-signing-keys. Even if a disgruntled current/former employee was somehow able to obtain to a device-signing-key (e.g. by accessing the merchants POS database), a device can still be re-initialised causing the previous device-signing-key to be invalidated.

So what is the process for device initialisation?

1. Retailer provisions a new globably-unique-device-ID (GUDID) from the Oxipay merchant portal.
2. During the setup/initialisation of a new POS terminal; the technition would enter the merchant-ID and the provisioned GUDID, and then perform some action to issue a request to the CreateKey operation. The CreateKey request would be signed with the GUDID.
3. Oxipay would return a device-signing-key and flag the GUDID as 'in use' meaning it can ***never*** be used again as a signing-key - essentially the GUDID can only be used as a signing key once.
4. The POS terminal would securely record the device-signing-key, which will be used to sign all subsequent requests to Oxipay.

Couple additional points to mention:

* GUDIDs should be provisioned on an 'as needed' basis. If a merchant decided to provision say 100 up-front, a malicious current employee with access to this functionality in the merchant portal could potentially use one of the GUDIDs that is not 'in use' to create their own device-signing-key.
* As mentioned re-initialising a device can be done as often as needed. A new GUDID however, will need to be provisioned for each attempt. 