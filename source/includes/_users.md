# Users

The users in Tutory are managed using different roles. 

* GET /api/v1/users
* GET /api/v1/users/me
* GET /api/v1/users/:id
* PUT /api/v1/users/:id
* DELETE /api/v1/users/:id
* POST /api/v1/users/


## Get all users

###### <verb class="get">GET</verb> /api/v1/users

This endpoint can be used to retrieve a list of users. With this endpoint it is possible to:

* Sort the users to be returned
* Select the fields to be returned
* Specify a search criteria for users
* Specify the amount of users to retrieve per page and the page number

<aside class="notice">
User needs to be granted the <code>users.index</code> role to call this endpoint.
</aside>

### Parameters
When a user makes the request, users are returned with the following attributes:

Attributes | Type | Description
-------- | ----- | -----------
first-name | string | The user's first name
last-name | string | The user's last name
birthday | object  | The user's date of birth
nationality | string | The user's nationality
tutor | boolean | `true` if the user is a tutor
student | boolean | `true` if the user is a student
active | boolean | `false` if the user has been deleted
avatar | object | The user's profile picture
created-at | date | The date where the user joined Tutory
updated-at | date | The date where the user joined Tutory
currency | string | The currency used by the user
time-zone | string | The time zone of the user. See <a href="#time-zones">Time Zone</a> below
locale | string | The preferred language of the user
external-id | string | A unique id identifying the user
email | string | The user's primary email address
phone | string | The user's primary phone number. See Phone Number below

### Include
* `identities`: All the identities of the user (refer to <a href="#get-all-identities">identities</a>).
* `roles`: All the roles attach to each user (refer to <a href="#get-all-roles">roles</a>).

## Get a user

###### <verb class="get">GET</verb> /api/v1/users/:id

This endpoint can be used to retrieve user details given the user `id`.

### Parameters

Attributes | Type | Private | Description
-------- | -----| -------- | -----------
first-name | string | no | The user's first name
last-name | string | yes | The user's last name
birthday | object | yes* | The user's date of birth
age | object | no | The age range of the user (min and max)
nationality | string | yes | The user's nationality
tutor | boolean | no | `true` if the user is a tutor
student | boolean | no | `true` if the user is a student
active | boolean | no | `false` if the user has been deleted
avatar | object | no | The user's profile picture
created-at | date | no | The date where the user joined Tutory
updated-at | date | yes* | The date where the user joined Tutory
currency | string | no | The currency used by the user
time-zone | string | no | The time zone of the user. See <a href="#time-zones">Time Zone</a> below
locale | string | no | The preferred language of the user
external-id | string | no | A unique id identifying the user
email | string | yes* | The user's primary email address
phone | string | yes | The user's primary phone number. See Phone Number below
notes | string | yes** | Notes written about a user

\* These fields are only accessible by the owner and admins.

\** This field is only accessible by an admin.

### Protected fields

User attributes are not all accessible by default. 
The protected fields of a user are accessible for:

* user granted with a `users.show` role.
* user viewing its own profile.
* user viewing a booked tutor (booking must be active).

### Include
* `identities`: All the identities of the user (refer to <a href="#get-all-identities">identities</a>).
* `roles`: All the roles of the user (refer to <a href="#get-all-roles">roles</a>).


## Get my details

###### <verb class="get">GET</verb> /api/v1/users/me

This endpoint can be used to retrieve the user's details.

It has the same parameters and inclusion as the <a href="#get-a-user">Get a user</a> endpoint.


## Create a user

###### <verb class="post">POST</verb> /api/v1/users

This endpoint can be used to sign-up a new user.


## Update a user

###### <verb class="put">PUT</verb> /api/v1/users/:id

This endpoint can be used to update user details given the user `id`.

<aside class="notice">
A user can only update its own account, unless it is granted a <code>users.update</code> role.
</aside>

### Side effects

* Updating the phone number will require new phone verification.
* Updating the email will require new email verification.


## Remove a user

###### <verb class="delete">DELETE</verb> /api/v1/users/:id

This endpoint can be used to delete a user account given the user `id`.
The user's `active` attribute will be set to `false`.

<aside class="notice">
A user can only delete its own account, unless it is granted a <code>users.destroy</code> role.
</aside>
