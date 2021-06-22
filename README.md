# Cumulocity Postman Collection v2
Cumulocity Postman collection compliant with the latest V2 format [JSON](https://github.com/AdeelChohan/cumulocity-postmanv2/blob/main/V2-%20Cumulocity_API.postman_collection.json)

The source of the API is the previously supported V1 Cumulocity Postman collection. v1 collections are no longer supported by Postman and Software AG RnD no longer maintains them due to the switch to the OpenAPI specification. The collection may contain old endpoints that may no longer be supported on version 10.9. 

`https://app.getpostman.com/run-collection/7c7d00719ab238097686`

The collection has been converted using the offical Postman Collection Transformer tool from V1 to V2

`https://learning.postman.com/docs/getting-started/importing-and-exporting-data/#converting-postman-collections-from-v1-to-v2`

## Prerequisites

- *Postman* The collection is for use by the Postman app. Postman is a utility that allows you to quickly test and use REST APIs. More information can be found at [getpostman.com](https://www.getpostman.com/).
- *Cumulocity* - To use our API, you must have valid credentials. Reach out to Software AG support if you need access to it. 
- *Tenant ID* - You can call `GET /tenant/currentTenant` with valid credentials. More information [here](http://cumulocity.com/api/#section/Authentication).

The authorization header is formed as `Basic <Base64(<tenantID>/<c8yuser>:<password>)>`.  
  
For instance, if your tenantID, username and password are t0071234, testuser and secret123 respectively, you can generate the Base64 string with the following command:
  
`$ echo -n t0071234/testuser:secret123 | base64`

and your authorization header would look like this:

` "Authorization": "Basic dDAwNzEyMzQvdGVzdHVzZXI6c2VjcmV0MTIz" `

You can also use  [base64encode.org](https://www.base64encode.org) to generate the Base64 string



## Usage
Graphical REST clients such as Postman are a convenient way to explore REST interfaces and the Cumulocity IoT database content.

Cumulocity IoT provides numerous online API examples. If you want to make use of them, download and install  [Postman](https://www.postman.com) . After starting Postman, you can choose to either create an account or click Take me straight to the app. Then click the button below and choose the variant of Postman that you have just installed. You may see a browser security prompt asking you if you actually want to run Postman (on Windows “Electron”).

![alt text](https://cumulocity.com/guides/images/rest/postman.png)

Import the APIs as a [V2 JSON](https://github.com/AdeelChohan/cumulocity-postmanv2/blob/main/V2-%20Cumulocity_API.postman_collection.json) file.

Now, click the Collections tab on the top left of Postman. You should see a folder Cumulocity API with the examples. Open that folder and the subfolder Alarms, then click Get collection of alarms. This shows an example on how to get alarms from Cumulocity IoT.

Note that the example contains placeholders, in this case a placeholder {{url}} in {{url}}/alarm/alarms. You need to tell Postman how to fill these placeholders and by this, how to connect to your Cumulocity IoT account. To do so, create an environment and configure the placeholders.

- Click on the cogwheel on the top right and choose Manage Environments, then click Add.
- Enter a name for the environment (e.g., your tenant ID), then add values for the placeholders.
- Configure a key url with a value of https://<yourTenant>.cumulocity.com. Click Submit.
- Configure a key auth with the value of the Authorization header for the REST requests.
- Click Add, then close the dialog. Now select your newly created environment from the drop-down box on the top right, that initially reads “No environment”.


|Variable  |Sample value               |Comments          
|----------|----------------------------|---------------
|`url` | `https://myown.us.cumulocity.com` |Replace with your own environment URL               
|`auth`|`Basic dDAwNzEyMzQvdGVzdHVzZXI6c2VjcmV0MTIz` |     Format is `Basic <Base64(<tenantID>/<c8yuser>:<password>)>`

More information on managing Postman environments and variables can be found [here](https://www.getpostman.com/docs/v6/postman/environments_and_globals/variables).

