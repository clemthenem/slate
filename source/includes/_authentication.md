# Authentication

Tutory uses Auth0 (https://auth0.com/) to authenticate users.

In order to get a valid **JWT token** (necessary to connect to the platform), you need to get an auth0 **code**.

The code provided by auth0 allows to verify that you have correctly logged in.

Once you've logged in on the website you should be redirected and get a **code** in the url.

### Get the auth0 code

#### Developer environment (localhost)

<a target="_blank" href="https://tutory.au.auth0.com/login?response_type=code&client=oGWa3mqDY60HfZ2faphy668XQkYj0Kqm&scope=openid%20email">Login here</a>
 to get your auth0 code.

> To get a JWT token, use this code:

```shell
curl --request POST \
  --url https://tutory.au.auth0.com/oauth/token \
  --header 'Cache-Control: no-cache' \
  --data 'grant_type=authorization_code&
          client_id=<CLIENT_ID_ENV>&
          client_secret=<CLIENT_SECRET_ENV>&
          code=<YOUR_CODE>&
          redirect_uri=http://localhost:3000'
```

> Make sure to replace `YOUR_CODE` with the code your received when you logged in.

> The above command returns JSON structured like this:

```json
{
  "access_token": "<ACCESS_TOKEN>",
  "id_token":"<JWT_TOKEN>",
  "expires_in":86400,
  "token_type":"Bearer"
}
```

### Get the JWT token

#### Developer environment (localhost)

parameter | Value
--------- | -----------
client_id | oGWa3mqDY60HfZ2faphy668XQkYj0Kqm
client_secret | Request the client secret key to a tutory dev.

#### UAT environment (test)

parameter | Value
--------- | -----------
client_id | COXnPaljg1djx235QKBbHRFZVOHH4sFy
client_secret | Request the client secret key to a tutory dev.

#### Production environment (live)

<aside class="notice">
TODO
</aside>


You are now ready to communicate with the other endpoints of the Tutory API.
