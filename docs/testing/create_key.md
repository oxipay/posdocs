The following documents some canned responses for testing the <a href="/api/create_key/">CreateKey</a> API.



**Fake Key for generate the signature: "1234567890"**

**Assumptions:**

1. All required parameters must be populated.
2. HMAC has been correctly generated and assigned as the request signature.
3. Invaild signature will return a "Failed" StatusCode.
4. Any request paramters combindation that not listed below will return Error Status

**Method:** *CreateKey*

**StatusCode OutComes by Request Parameters**
**Notes.**
"####" means any 4 charaters

StatusCode | clientDeviceId 
-----------|----------------
Success | 1 
Failed  | 2 
Error   | 3
