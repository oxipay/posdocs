## Device Initialisation / Setup

<strong>API reference: <a href="/resources/api_reference/#create-key">CreateKey</a></strong>

This section describes the process of registering a POS device with Oxipay. This registration process will ensure that Oxipay registers the POS device with a unique identifier and issues a device specific key that can be used by that device to digitally sign all traffic.

Every POS device will have to be registered with Oxipay before initiating an Oxipay transaction.

Steps:

 1. POS technician wants to register a terminal.
    * **Option 1:** Merchant can request a list of unique device Ids directly from Oxipay. Oxipay can provide them with this, which then will have to handed over to POS technician

    * **Option 2:** He can log into Oxipay POS Portal and add a device. He will be required to enter the actual device id (internal to POS – assuming these are unique across the system). A unique Oxipay Device Id will be generated for that terminal. There will be facility to bulk generate these ids.

 2. Once the POS technician has the Oxipay Device ID, he can invoke the DeviceSetup API from the terminal.

<strong>Notes:</strong>

 * The oxipay device ids are for one time use only. Once used, Oxipay will invalidate them.
 * The oxipay device ids will have an expiration time (yet to decide how long)
 * The final goal is to have the POS portal fully functional, including ability of user management. 

