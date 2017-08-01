<h3>API Versioning</h3>

The inspiration for our approach to versioning can be found in the following blog:<br/>
<a href="https://www.troyhunt.com/your-api-versioning-is-wrong-which-is/">Your API versioning is wrong, which is why I decided to do it 3 different wrong ways</a><br/>

Basically, we've provided 3 ways to specify an API version. As a consumer, you're free to choose whichever one you like:

1. **URL**: You simply whack the API version into the URL, for example <code>https://subdomain.oxipay.com.au/soap/v1/Service.svc?wsdl</code> (for SOAP) and <code>https://subdomain.oxipay.com.au/webapi/v1/operation</code> (for HTTP).
2. **Custom request header**: You use a URL that doesn't contain a version, but add a custom <code>api-version</code> HTTP header e.g. <code>api-version: #</code>, where # is the version number.
3. **Accept header**: You modify the accept header to specify the version, for example <code>Accept: application/vnd.oxipay.v2</code>

<h3>Versions</h3>

Version | Description | Publish date
-----------|-----------|-----------
v1 | Initial version | 01/08/2017
