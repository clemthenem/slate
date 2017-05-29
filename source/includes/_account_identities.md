# Account Identities

The account identity represents an object uniquely identifying a user.
A user may have one or many identities (way of connecting to the platform). 
Each identity is uniquely identified by an auth0_id provided by auth0.

## Get all account identities

###### <verb class="get">GET</verb> /api/v1/users/:id/identities

This endpoint can be used to retrieve a list of user identities. With this endpoint it is possible to:

* Sort the user's identities to be returned
* Select the fields to be returned
* Specify a search criteria for user identities
* Specify the amount of user identities to retrieve per page and the page number

### Parameters

Attributes | Type | Description
-------- | ----- | -----------
primary | boolean | `true` if it's the primary identity of the account 
value | string | The value of the identity (can be an email, a phone ...)
auth0-id | string | The unique auth0's id for this user identity
provider | string | The identity's provider (facebook, google, password-email...)
verified | boolean | `true` if the identity has been verified by auth0
created-at | date | The creation date of the identity
updated-at | date | The last time the identity has been updated

## Get an identity

###### <verb class="get">GET</verb> /api/v1/account/identities/:id

### Parameters


## Link a user identity

###### <verb class="post">POST</verb> /api/v1/account/identities

### Parameters

Attributes | Type | Required | Description
---------- | ---- | -------- | -----------
link-with | string | yes | The JWT of the secondary account being linked


## Update an identity

###### <verb class="put">PUT</verb> /api/v1/account/identities/:id

This endpoint can be used to modify the primary account's identity.

### Parameters

Attributes | Type | Required | Description
---------- | ---- | -------- | -----------
primary | boolean | no | `true` if it's the primary identity of the account 

## Remove an identity

###### <verb class="delete">DELETE</verb> /api/v1/account/identities/:id
