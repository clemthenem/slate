# Account Verifications

Account verifications are used to ensure integrity of a user.

### Verification types

There are several types of verification available to you:

* __Phone Verification__

Verify the current phone number of a user by sending him a text message.

Description | Limitation
----------- | -----------
Number of refresh token before blocked | 3 times
Number of attempts before refreshing token | 3 times
Token lifetime before expiring | 20 minutes
Lifetime | Until phone changes

* __Email Verification__

Verify the current email of a user by sending him a verification email.

Description | Limitation
----------- | ----------
Number of refresh token before blocked | 5 times
Number of attempts before refreshing token | 5 times
Token lifetime before expiring | 3 days
Lifetime | Until email changes

### Include

The following resources can be included in the response.

* `verification-type`: Details of the type of verification.
* `user`: The owner of the verification and all its details.

### Verification status
* `created`: The verification has been created and no action has been started.
* `pending`: The verification is waiting for an intervention (user or admin).
* `verified`: The verification has been verified and is valid.
* `canceled`: The verification was canceled before being verified.
* `expired`: The verification expired after updating user's field or an admin action.
* `blocked`: The verification was blocked after too many attempts or by an admin.


## Get all verifications

###### <verb class="get">GET</verb> /api/v1/account/__verifications__/

This endpoint can be used to retrieve a list of verifications. With this endpoint it is possible to:

* Sort the verifications to be returned
* Select the fields to be returned
* Specify a search criteria for verifications
* Specify the amount of verifications to retrieve per page and the page number

### Parameters

Attributes | Type | Admin | Description
---------- | ---- | ----- | -----------
status | string | no | The current status of the verification `created`, `pending`, `verified`, `expired`, `canceled`, `blocked`
token-expired-at | date | no | The time where the token is going to expire
approved-at | date | no | The time where the verification has been approved
verification-number | string | no | Possible reference of a verification in another system
attempts | integer | no | The number of time a user has been trying to verify the token
token-counter | integer | no | The number of  token generation
created-at | date | no | The creation date of the verification
updated-at | date | no | The last time the verification has been updated
locale-key | string | no | The slug type of the verification `email`, `phone`
additional-info | text | yes | Extra details regarding a verification.
method | string | yes | How the verification has been processed `automatic`, `manual`...
approved-by | integer | yes | The user's ID that approved the verification, if any.

<aside class="warning">
A user can only list the verifications of its own account, unless it is granted a <code>verifications.*****</code> role.
</aside>

## Get a verification

###### <verb class="get">GET</verb> /api/v1/account/__verifications/:id__

### Parameters

Attributes | Type | Admin | Description
---------- | ---- | ----- | -----------
status | string | no | The current status of the verification `created`, `pending`, `verified`, `expired`, `canceled`, `blocked`
token-expired-at | date | no | The time where the token is going to expire
approved-at | date | no | The time where the verification has been approved
verification-number | string | no | Possible reference of a verification in another system
attempts | integer | no | The number of time a user has been trying to verify the token
token-counter | integer | no | The number of  token generation
created-at | date | no | The creation date of the verification
updated-at | date | no | The last time the verification has been updated
locale-key | string | no | The slug type of the verification `email`, `phone`
additional-info | text | yes | Extra details regarding a verification.
method | string | yes | How the verification has been processed `automatic`, `manual`...
approved-by | integer | yes | The user's ID that approved the verification, if any.

<aside class="notice">
A user can only get the verifications of its own account, unless it is granted a <code>verifications.show</code> role.
</aside>

## Create a verification

###### <verb class="post">POST</verb> /api/v1/account/__verifications__

### Parameters

Attributes | Type | Required | Description
---------- | ---- | -------- | -----------
verification-type-slug | string | yes | The type of verification you would like to create <a href="#verification-types">find the list here</a>.
verification-number | string | no | An external id link to this verification

<aside class="notice">
A user can only create a verification for its own account, unless it is granted a <code>verifications.create</code> role.
</aside>

### Result

Each verification creation will involve a different behavior dependent on the <a href="#verification-types">verification type</a>.

### Errors

* __750__: The type of verification is invalid. Make sure you use the correct <a href="#verification-types"> verification type</a>.
* __751__: A verification with the current parameters already exists and has been verified.
* __752__: A verification with the current parameters already exists and is pending. You cannot create a new one unless you cancel this.

## Refresh a verification

###### <verb class="put">PUT</verb> /api/v1/account/__verifications/:id__

You can refresh the token of a verification several times if it was expired or lost.
The maximum number of refresh token depends on <a href="#verification-types">the type of verifications.</a>

After that the verification will be blocked and the user will not be able to create/verify/refresh any verification.

<aside class="warning">
A user will be blocked if it reaches the maximum number of refresh attempts.
</aside>

### Parameters required
The following parameters should be included in the request to refresh a token.

Attributes | Type | Value
---------- | ---- | -----
action | string | `refresh`

<aside class="notice">
A user can only refresh its own verifications or its pupil's ones.
</aside>

### Errors

* __753__: The verification has been blocked after too many refresh. Contact an administrator.
* __754__: There is a delay of 1 minute between each refresh. Wait and try again.
* __755__: You have reached the limit of refresh tokens, the account has been blocked and cannot do any operations with verifications.
* __757__: The verification cannot be refreshed as it is expired or canceled, create a new one.


## Validate a verification

###### <verb class="put">PUT</verb> /api/v1/account/__verifications/:id__

This endpoint allows to end the process of basic verifications. Some verification cannot be done 
by the user himself and requires an external/admin action (identity verification etc.).
The user will have a limited number of attempts for its verification described in each <a href="verification-types">verification type</a>.

### Parameters required
The following parameters needs to be included in the request to be successfully verified.

Attributes | Type | Value | Description
---------- | ---- | ----- | -----------
action | string | `verify` | Describe the type of action
verify-token | string | `<token-sent>` | Token generated and sent at the creation/refresh.

<aside class="notice">
A user can only verify its own verification or its pupil's one.<br/>
</aside>

<aside class="notice">
Some verification do not require authentication (eg: email verification)
</aside>


### Errors

* __756__: You had too many unsuccessful attempts to verify a token. Try to refresh the token.

## Update a verification

###### <verb class="put">PUT</verb> /api/v1/account/__verifications/:id__

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
status | string | Status of the verification: <a href="#verification-status" available here</a>
method | string | How the verification has been processed `automatic`, `manual`...
additional-info | text | Attach more details to a verification
verification-number | string | Possible reference of a verification in another system
verify-token | string | Token to compare with the verification token.
action | string | `refresh`, `verify` actions used in <a href="#validate-a-verification">verification validation</a> or <a href="#refresh-a-verification">refresh token</a>

<aside class="notice">
A user can only update a verification if it is granted a <code>verifications.update</code> role.
</aside>


## Remove a verification

###### <verb class="delete">DELETE</verb> /api/v1/account/__verifications/:id__

This endpoint will expire the given verification if verified or cancel it if pending/created.

<aside class="notice">
A user can only remove its account verifications unless it is granted a <code>verifications.destroy</code> role.
</aside>
