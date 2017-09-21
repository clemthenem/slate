# Competences

This section is one of the key section to find a tutor on the platform.
Tutors can add competences to their profile and students can search them.

## Search competences

###### <verb class="get">GET</verb> /api/v1/__competences__

This endpoint will return the user's competences by default.

### Parameters

Some parameters are also defined in the tutor's profile. 
This allow to have a custom behaviour for each competence as well as a general one.

Attributes | Type | Filter | Description
---------- | -----| ------ | -----------
first-lesson-free | boolean | true | `tutor_profile.first_lesson_free` is the one by default, first lesson for this subject is free
custom-level | string | true | Allows user to define a custom level (e.g: "Black Belt" for judo etc.)
level | string | true | Allows to get an idea of the tutor's level for a subject.
last-subject-update | date | true | Gives the last time the tutor reviewed the details of the subject. It allows to notify tutors when a subject changes.
min-lesson-duration | integer | false | Gives the minimum duration of a lesson.
min-lesson-frequency-unit | string | false | Gives the unit of the lesson frequency (month, week...)
min-lesson-frequency-value | integer | false | Gives the value of the lesson frequency (1,3,4 times)
subject-id |integer | true | The unique identifier of a subject on tutory-tree.
created-at | datetime | false | Date of the competence's creation.
updated-at | datetime | false | Date of the last competence's update.
visible | datetime | true | `true` if the competence is publicly visible. The tutor will be able to access it even if it's set to not visible.

### Filters

The parameters marked by `true` in the filter column can be used. Filters can be combined to get more specific results.

#### Modified filter behaviour

* `subject-id`: Filter the list of ids of subjects of interest (separated by comas). 

By default the competences of the tutor are selected. 

Administrators granted by the `competences.search` role can use the `all` value to get all the subjects.

E.g: __filter[subject-id]__=125,128


#### Additional filters

Additional filters have been added:

* `distance`: `<distance>,<latitude>,<longitude>` - Filter the competences taught in a given area (1km - 20km radius)

E.g: __filter[distance]__=10,-33.9490543,151.2557003 

This will return the competences taught within 10 kilometers from Maroubra Beach as well as other 
competences taught further away but with the possibility of coming to the user's home or online.

* `class-type`: Filter the type of classes offered for teaching this competence. 
    - `elsewhere`: Competence that can be taught face to face anywhere.
    - `group`: Competence that can be taught to a group.
    - `online`: Competence that can be taught online.
    - `student-home`: Competence that can be taught at the student's home.
    - `tutor-home`: Competence that can be taught at the tutor's home.
    
E.g: __filter[class-type]__=student-home,online 

This will return the competences that are taught at the student home or online.


### Sorting

This is setup by default.
* `tutor_profile.address.distance`: Sort by the distance separating the user from the tutor (closest to furthest).

### Include

<aside class="warning">
At the moment, there is a bug when `include=user,tutor-profile`. 
Make sure you include tutor-profile first: `include=tutor-profile,user`.
</aside>

* `tutor-profile`: Include the tutor-profile associated to that competence
* `user`: Get the user through the tutor-profile association.
* `price-listings`: Get the different price listings associated.
* `price-listing-defaults`: Get the different defaults price listings included in the price listing set (if any).
* `price-listing-set`: Get the set of price listings attached to the tutor profile.


## Get a competence

###### <verb class="get">GET</verb> /api/v1/__competences/:id__

This endpoint will return the competence requested.

### Parameters

Some parameters are also defined in the tutor's profile. 
This allow to have a custom behaviour for each competence as well as a general one.

Attributes | Type | Filter | Description
---------- | -----| ------ | -----------
first-lesson-free | boolean | true | `tutor_profile.first_lesson_free` is the one by default, first lesson for this subject is free
custom-level | string | true | Allows user to define a custom level (e.g: "Black Belt" for judo etc.)
level | string | true | Allows to get an idea of the tutor's level for a subject.
last-subject-update | date | true | Gives the last time the tutor reviewed the details of the subject. It allows to notify tutors when a subject changes.
min-lesson-duration | integer | false | Gives the minimum duration of a lesson.
min-lesson-frequency-unit | string | false | Gives the unit of the lesson frequency (month, week...)
min-lesson-frequency-value | integer | false | Gives the value of the lesson frequency (1,3,4 times)
subject-id |integer | true | The unique identifier of a subject on tutory-tree.
created-at | datetime | false | Date of the competence's creation.
updated-at | datetime | false | Date of the last competence's update.
visible | datetime | true | `true` if the competence is publicly visible. The tutor will be able to access it even if it's set to not visible.

### Include

<aside class="warning">
At the moment, there is a bug when `include=user,tutor-profile`. 
Make sure you include the tutor-profile first if you request the user too: `include=tutor-profile,user`.
</aside>

* `tutor-profile`: Include the tutor-profile associated to that competence
* `user`: Get the user through the tutor-profile association.
* `price-listings`: Get the different price listings associated.
* `price-listing-defaults`: Get the different defaults price listings included in the price listing set (if any).
* `price-listing-set`: Get the set of price listings attached to the tutor profile.


## Create a competence

###### <verb class="post">POST</verb> /api/v1/__competences__

Use this endpoint to add a new competence to the tutor profile.

### Parameters

Some parameters are also defined in the tutor's profile. 
This allow to have a custom behaviour for each competence as well as a general one.

Attributes | Type | Description
---------- | ---- | -----------
first-lesson-free | boolean | `tutor_profile.first_lesson_free` is the one by default, first lesson for this subject is free
custom-level | string | Allows user to define a custom level (e.g: "Black Belt" for judo etc.)
level | string | Allows to get an idea of the tutor's level for a subject.
min-lesson-duration | integer | Gives the minimum duration of a lesson.
min-lesson-frequency-unit | string | Gives the unit of the lesson frequency (month, week...)
min-lesson-frequency-value | integer | Gives the value of the lesson frequency (1,3,4 times)
subject-id |integer | The unique identifier of a subject on tutory-tree.
visible | datetime | `true` if the competence is publicly visible. The tutor will be able to access it even if it's set to not visible.


## Update a competence

###### <verb class="put">PUT</verb> /api/v1/__competences/:id__

<aside class="notice">
A user can only remove one of his competence unless he is granted a <code>competences.update</code> role.
</aside>

### Parameters

Some parameters are also defined in the tutor's profile. 
This allow to have a custom behaviour for each competence as well as a general one.

Attributes | Type | Description
---------- | ---- | -----------
first-lesson-free | boolean | `tutor_profile.first_lesson_free` is the one by default, first lesson for this subject is free
custom-level | string | Allows user to define a custom level (e.g: "Black Belt" for judo etc.)
level | string | Allows to get an idea of the tutor's level for a subject.
min-lesson-duration | integer | Gives the minimum duration of a lesson.
min-lesson-frequency-unit | string | Gives the unit of the lesson frequency (month, week...)
min-lesson-frequency-value | integer | Gives the value of the lesson frequency (1,3,4 times)
subject-id |integer | The unique identifier of a subject on tutory-tree.
visible | datetime | `true` if the competence is publicly visible. The tutor will be able to access it even if it's set to not visible.


## Remove a competence

###### <verb class="delete">DELETE</verb> /api/v1/__competences/:id__

<aside class="notice">
A user can only remove one of his competence unless he is granted a <code>competences.destroy</code> role.
</aside>
