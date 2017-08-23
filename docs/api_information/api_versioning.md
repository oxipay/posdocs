<h3>API Versioning</h3>

We implement a basic URL based versioning scheme, as this is the easiest scheme for clients to consume because the API is directly part of the URL and no special headers are needed.

The API version is simply included into the URL as follows: <code>https://subdomain.oxipay.com.au/soap/<font style="background-color: yellow;">v1</font>/Service.svc?wsdl</code> (for SOAP) and <code>https://subdomain.oxipay.com.au/webapi/<font style="background-color: yellow;">v1</font>/operation</code> (for HTTP).<br/>

**Note**: There is no "fallback" behaviour if the version number is excluded from the URL (i.e. will be a 404 not found response rather than calling v1 or the latest version). This decision was made to avoid confusion over which version of the API is being executed.

<h3>Versions</h3>

Version | Description | Publish date
-----------|-----------|-----------
v1 | Initial version | 01/08/2017
