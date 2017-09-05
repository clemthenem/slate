# Profile Translations

Users may add many translations of their profile (tutor/student).


## Get all profile translations

###### <verb class="get">GET</verb> /api/v1/__profile-translations__

<aside class="notice">
User needs to be granted the <code>profile-translations.index</code> role to call this endpoint.
</aside>

This endpoint allows to retrieve all the profile translations.

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
locale | string | The language code of the translation. E.g: "en-AU".
headline | text | The headline of the profile.
description | text | The description of the profile.

### Include

* `tutor-profile`: The tutor profile associated to the translation.


## Get a profile translation

###### <verb class="get">GET</verb> /api/v1/__profile-translations/:id__

This endpoint allows to retrieve a specific profile translation.

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
locale | string | The language code of the translation. E.g: "en-AU".
headline | text | The headline of the profile.
description | text | The description of the profile.

### Include

* `tutor-profile`: The tutor profile associated to the translation.


## Create a profile translation

###### <verb class="post">POST</verb> /api/v1/__profile-translations__

```json
{
	"data": {
		"type": "profile-translations",
		"attributes": {
			"locale": "en-AU",
			"description": "I'm an enthusiastic tutor! Yeah!"
		},
		"relationships": {
			"tutor-profile": {
				"data": {
    				"type": "tutor-profiles", 
    				"id": "<tutor_profile_id>"
    			}
			}
		}
	}
}
```

This endpoint allows to create a new profile translation associated to a tutor/student profile.

### Parameters

Attributes | Type | Required | Description
---------- | -----| -------- | -----------
locale | string | yes | The language code of the translation. E.g: "en-AU".
headline | text | no | The headline of the profile.
description | text | no | The description of the profile.

### Errors

* __100__: A translation in this language already exists for this profile, update it.
* __403__: You are not allowed to create a translation for another user.


## Update a profile translation

###### <verb class="put">PUT</verb> /api/v1/__profile-translations/:id__

This endpoint allows to update a given profile translation.

<aside class="notice">
User can only update their profile translation or needs to be granted the 
<code>profile-translations.update</code> role to call this endpoint.
</aside>

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
locale | string | The language code of the translation. E.g: "en-AU".
headline | text | The headline of the profile.
description | text | The description of the profile.


## Delete a profile translation

###### <verb class="delete">DELETE</verb> /api/v1/__profile-translations/:id__

This endpoint allows to delete a given profile translation.

<aside class="notice">
User can only delete their profile translation or needs to be granted the 
<code>profile-translations.delete</code> role to call this endpoint.
</aside>
