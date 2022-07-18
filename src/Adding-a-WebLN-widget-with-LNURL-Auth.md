# Adding a WebLN widget with LNURL-Auth

Breez integrates various WebLN widgets in its Apps screen. When a widget also needs to authenticate the user using LNURL-Auth, the following process must be executed:

### Getting the LNURL-Auth URL
1. The vendor provides Breez with a predefined endpoint to get a valid LNURL for authentication (the same URL users typically get by scanning a QR code). Breez executes a GET request to this URL, and the vendor should respond with a JSON payload similar to: 
<code>{“lnurl_auth”:“lnurl1dp68gurn8ghj7ctsdyhxkmmvd35kgetj9eu8j730wccj7ct4w35z7etcw3jhymnpdshkcmjld3hkw6tw8a6xzeead3hkw6twye4nz0fkvv6kzepjx3skgefcxvmrvdf5xsuxvvp3xcenvdnzv9jk2en9xp3njcfexfjnze3evenr2cfhv93rjvehx56n2wrrxqckxvpjxgmrs2ayx7u”}</code>
2. Breez then extracts the LNURL from the JSON payload and initiates the LNURL-Auth process as defined in the spec.
3. On [step 3](https://github.com/fiatjaf/lnurl-rfc/blob/luds/04.md) of the LNURL-Auth protocol, Breez appends a query parameter **jwt=true** to the request.
4. The vendor service should then detect the jwt query parameter and respond with a jwt property as part of the json payload, for example: 
<code>{“status”: “OK”, “token”: [token]}</code>

### Using the jwt token in a web page
1. Breez opens the vendor web page in a web view and appends the token=[token] to the query parameters of the URL.
2. The vendor authenticates and logs the user in according to the token provided. 
