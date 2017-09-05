# Tutor Profile

User may create a tutor profile on their account. This profile is automatically created when the `tutor` field
is enabled in their user account. There is only one tutor profile per user.

Tutory requires a minimum age (16 years old) in order to become a tutor.
Below this age the user will not be able to update or view its tutor profile.

### Cancellation policies

The cancellation policies define the amount refunded when a student cancels its lesson.

* `48_hours_no_refund`: No refund if cancellation happens less than 48 hours before a lesson.
* `24_hours_no_refund`: No refund if cancellation happens less than 24 hours before a lesson.
* `48_hours_partial_refund`: Partial refund (__TODO__ to be discussed) if cancellation happens less than 48 hours before a lesson.
* `24_hours_partial_refund`: Partial refund (__TODO__ to be discussed) if cancellation happens less than 24 hours before a lesson.
* `full_refund`: Full refund when a student cancels its lesson, no matter when.


## Get all tutor profiles

###### <verb class="get">GET</verb> /api/v1/__tutor-profiles__

<aside class="notice">
A user can list tutor profiles if he is granted a <code>tutor-profiles.index</code> role.
</aside>

### Parameters

Attributes | Type | Description
---------- | -----| -----------
allow_face_to_face_classes | boolean | `true` if the tutors allows face to face classes
allow_group_classes | boolean | `true` if the tutors allows group classes
allow_online_classes | boolean | `true` if the tutors allows online classes
allow_student_home_classes | boolean | `true` if the tutors allows classes at the student home
allow_tutor_home_classes | boolean | `true` if the tutors allows classes at his home.
cancellation_policy | integer | Defines the cancellation policy of the tutor. <a href="#cancellation-policies">List here.</a>
first_lesson_free | boolean | `false` by default, first lesson with this tutor is free
max_number_of_students | integer | Maximum number of students allowed per lesson in a group.
min_lesson_duration | integer | Minimum time required for a lesson (minutes). E.g: 120 (minutes)
min_lesson_frequency_value | integer | Minimum number of lessons per `min_lesson_frequency_unit`. E.g: 1 (per week)
min_lesson_frequency_unit | integer | Unit of the lesson frequency (week, month, year).
created_at | datetime | Date of the tutor profile creation.
updated_at | datetime | Date of the last tutor profile update.
visible | datetime | `true` if the tutor profile is publicly visible.

### Include
* `user`: The user attached to the tutor profile (refer to <a href="#get-all-user">users</a>).
* `profile-translations`: The translations attach to the tutor profile 
(refer to <a href="#get-all-profile-translations">profile translations</a>).

### Errors
* __401__ : Permission denied for not allowed users.


## Get a tutor profile

###### <verb class="get">GET</verb> /api/v1/__tutor-profiles/:id__

<aside class="notice">
A user can only view its profile as well as `visible` tutor profiles, unless he is granted a <code>tutor-profiles.show</code> role.
</aside>

### Parameters

Attributes | Type | Description
---------- | -----| -----------
allow_face_to_face_classes | boolean | `true` if the tutors allows face to face classes
allow_group_classes | boolean | `true` if the tutors allows group classes
allow_online_classes | boolean | `true` if the tutors allows online classes
allow_student_home_classes | boolean | `true` if the tutors allows classes at the student home
allow_tutor_home_classes | boolean | `true` if the tutors allows classes at his home.
cancellation_policy | integer | Defines the cancellation policy of the tutor. <a href="#cancellation-policies">List here.</a>
first_lesson_free | boolean | `false` by default, first lesson with this tutor is free
max_number_of_students | integer | Maximum number of students allowed per lesson in a group.
min_lesson_duration | integer | Minimum time required for a lesson (minutes). E.g: 120 (minutes)
min_lesson_frequency_value | integer | Minimum number of lessons per `min_lesson_frequency_unit`. E.g: 1 (per week)
min_lesson_frequency_unit | integer | Unit of the lesson frequency (week, month, year).
created_at | datetime | Date of the tutor profile creation.
updated_at | datetime | Date of the last tutor profile update.
visible | datetime | `true` if the tutor profile is publicly visible.

### Include
* `user`: The user attached to the tutor profile (refer to <a href="#get-all-user">users</a>).
* `profile-translations`: The translations attach to the tutor profile 
(refer to <a href="#get-all-profile-translations">profile translations</a>).

### Errors
* __401__ : Permission denied for not allowed users.


## Get my tutor profile

###### <verb class="get">GET</verb> /api/v1/__tutor-profiles/me__

This endpoint can be used to retrieve the tutor's profile.

It has the same parameters and inclusion as the <a href="#get-a-tutor-profile">Get a tutor profile</a> endpoint.


## Create a tutor profile

###### <verb class="put">PUT</verb> /api/v1/__users/:id__

A tutor profile is automatically associated when the field `tutor` is enabled in the <a href="#users">user account</a>. 

### Parameters

Attributes | Type | Value
---------- | -----| -----------
tutor | boolean | `true`

### Errors

* __731__ : The date of birth needs to be known in order to create a tutor profile.
* __800__ : If the user is too young he won't be able to create a tutor profile.


## Update a tutor profile

###### <verb class="put">PUT</verb> /api/v1/__tutor-profiles/:id__

<aside class="notice">
A tutor can only update its profile unless he is granted a <code>tutor-profiles.update</code> role.
</aside>

### Parameters

Attributes | Type | Description
---------- | -----| -----------
allow_face_to_face_classes | boolean | `true` if the tutors allows face to face classes
allow_group_classes | boolean | `true` if the tutors allows group classes
allow_online_classes | boolean | `true` if the tutors allows online classes
allow_student_home_classes | boolean | `true` if the tutors allows classes at the student home
allow_tutor_home_classes | boolean | `true` if the tutors allows classes at his home.
cancellation_policy | integer | Defines the cancellation policy of the tutor. <a href="#cancellation-policies">List here.</a>
first_lesson_free | boolean | `false` by default, first lesson with this tutor is free
max_number_of_students | integer | Maximum number of students allowed per lesson in a group.
min_lesson_duration | integer | Minimum time required for a lesson (minutes). E.g: 120 (minutes)
min_lesson_frequency_value | integer | Minimum number of lessons per `min_lesson_frequency_unit`. E.g: 1 (per week)
min_lesson_frequency_unit | integer | Unit of the lesson frequency (week, month, year).
visible | datetime | `true` if the tutor profile is publicly visible.

## Remove a tutor profile

###### <verb class="delete">DELETE</verb> /api/v1/__tutor-profiles/:id__

<aside class="notice">
A user can only remove a tutor profile if he is granted a <code>tutor-profiles.destroy</code> role.
</aside>
