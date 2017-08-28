# Account Confirmation

Once a user created its account, he will need to confirm it to ensure the integrity of the platform.

## Confirm a user account

###### <verb class="put">PUT</verb> /api/v1/__account/identities/:id__

This endpoint can be used to "activate the account" of a user, confirm its creation. 
A user can confirm its account by clicking on the link received by email.

Description | Limitation
----------- | -----------
Token lifetime | 3 days

### Parameters

All the following parameters are required for the request.

Attributes | Type | Value | Description
---------- | ---- | ----- | -----------
action | string | `verify` | The type of action
verification-token | string | - | The uniq token used to confirm the account creation.

### Errors

* __711__: The token provided is invalid.
* __712__: The token lifetime has expired, refresh the token.

## Refresh confirmation token

###### <verb class="put">PUT</verb> /api/v1/__account/identities/:id__

If the user has lost the confirmation email or its confirmation token expired this endpoint will 
generate a new token.

Description | Limitation
----------- | -----------
Number of refresh token or invalid attemps before blocked | 5 times
Delay between each token refresh | 10 minutes

### Parameters

The following parameter is required for the request.

Attributes | Type | Value
-------- | -----| -----------
action | string | `refresh` 

### Errors

* __713__: There is a delay between each refreshed token.
* __714__: The user has requested a new confirmation token too many times.
* __715__: The account is already confirmed.


