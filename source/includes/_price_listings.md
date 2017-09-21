# Price Listings

Price listings can be customized by competences or can be set by default by being associated to the tutor profile.

### Price listings categories

There are a number of different price listings categories available to the tutor. 
He can decides to give discounts when a student book a large number of hours.

* standard: Standard rate for a x of hours
* pack_x_hours: Price for x hours of classes.
* x_hours_a_week: Price for x hours of lesson a week.
* x_hours_a_month: Price for x hours of lesson a month.


## Get all price listings

###### <verb class="get">GET</verb> /api/v1/__price-listings__

<aside class="notice">
This endpoint is limited to administrator granted of the <code>price-listings.index</code> role.
</aside>

This endpoint returns all the price listings.

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
amount-home-lesson | float | Price requested by the tutor for a lesson at his home.
amount-travel-lesson | float |Price requested by the tutor for a lesson "outside".
amount-per-extra-student | float | Price per extra student during grouped lessons.
amount_web_lesson | float | Price of a lesson given online.
category | integer | One of the <a href='#price-listings-categories'>price-listing categories</a> specified.
currency | string | The currency of the price listing.
length |float | The time (hours) for this price listing.
created-at | datetime | Date of the price listing's creation.
updated-at | datetime | Date of the last price listing's update.


## Get a price listing

###### <verb class="get">GET</verb> /api/v1/__price-listings/:id__

Ths endpoint returns a particular price listing.

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
amount-home-lesson | float | Price requested by the tutor for a lesson at his home.
amount-travel-lesson | float |Price requested by the tutor for a lesson "outside".
amount-per-extra-student | float | Price per extra student during grouped lessons.
amount_web_lesson | float | Price of a lesson given online.
category | integer | One of the <a href='#price-listings-categories'>price-listing categories</a> specified.
currency | string | The currency of the price listing.
length |float | The time (hours) for this price listing.
created-at | datetime | Date of the price listing's creation.
updated-at | datetime | Date of the last price listing's update.

## Create a price listing

###### <verb class="post">POST</verb> /api/v1/__price-listings__

This endpoint adds a new price listing to a competence or to a price listing set (one or the other is required).

### Parameters

Attributes | Type | Required | Description
---------- | ---- | -------- | ------------
amount-home-lesson | float | false | Price requested by the tutor for a lesson at his home.
amount-travel-lesson | float | false | Price requested by the tutor for a lesson "outside".
amount-per-extra-student | float | false | Price per extra student during grouped lessons.
amount_web_lesson | float | false | Price of a lesson given online.
category | integer | true | One of the <a href='#price-listings-categories'>price-listing categories</a> specified.
currency | string | true | The currency of the price listing.
length |float | false | The time (hours) for this price listing.

### Association

To create a new price-listing, you must associate it to an existing <a href="#competences">competence</a> or price-listing-set (not both).


## Update a price listing

###### <verb class="put">PUT</verb> /api/v1/__price-listings/:id__

This endpoint allows to update a given price listing. 

<aside class="notice">
Users can only update their own price listings, unless they are granted a <code>price-listings.update</code> role.
</aside>

### Parameters

Attributes | Type | Required | Description
---------- | ---- | -------- | ------------
amount-home-lesson | float | false | Price requested by the tutor for a lesson at his home.
amount-travel-lesson | float | false | Price requested by the tutor for a lesson "outside".
amount-per-extra-student | float | false | Price per extra student during grouped lessons.
amount_web_lesson | float | false | Price of a lesson given online.
category | integer | true | One of the <a href='#price-listings-categories'>price-listing categories</a> specified.
currency | string | true | The currency of the price listing.
length |float | false | The time (hours) for this price listing.


## Delete a price listing

###### <verb class="delete">DELETE</verb> /api/v1/__price-listings/:id__

This endpoint allows to delete a given price listing. 

<aside class="notice">
Users can only delete their own price listings, unless they are granted a <code>price-listings.destroy</code> role.
</aside>
