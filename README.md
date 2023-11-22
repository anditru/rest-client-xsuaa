# REST Client Configuration for XSUAA

In the folder `template` you find a template configuration for VS Code's [REST Client extension](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) file to test APIs that are secured with SAP Authorization and Trust Management Service (XSUAA).

Before you can send requests to your API, complete the following steps:

1. Create an `.env` file in the same folder as your `.http` file and make sure it is gitignored. The .env file must have the following properties:

```
auth-url=
client-id=
client-secret=
srv-url=
```

`auth-url` represents the URL of XSUAA. Usually, something like `https://XXXXX.authentication.eu10.hana.ondemand.com` if you are on eu10.

`srv-url` is the URL of your API.

You can either create the file manually and fill it with the corresponding values from your application's service binding to XSUAA or, if your app runs in Cloud Foundry, execute the script `init-env.js` as follows:

```
node init-env.js <application name> <target folder>
```
Make sure you are logged in to Cloud Foundry before you execute the script and replace `<application name>` with the name of your application in Cloud Foundry and `<target folder>` with the path to the folder you want your `.env` file to be in.

2. Send the request "Get OAuth token" once to retrieve an access token.

Now you can query your API.