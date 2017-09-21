# Price Listing Sets

This entity allows to group several price listings.

## Get all price listing sets

###### <verb class="get">GET</verb> /api/v1/__price-listing-sets__

<aside class="notice">
This endpoint is limited to administrator granted of the <code>price-listing-sets.index</code> role.
</aside>

This endpoint returns all the price listing sets.

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
name | string | The name given to the price listing set.
created-at | datetime | Date of the price listing set's creation.
updated-at | datetime | Date of the last price listing set's update.

### Include

* `price-listings`: All the <a href="#price-listings">price listings</a> included in the price listing set.
* `tutor-profile`: The <a href="#tutor-profiles">tutor profile</a> associated to the price listing set.

## Get a price listing set

###### <verb class="get">GET</verb> /api/v1/__price-listing-sets/:id__

Ths endpoint returns a particular price listing.

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
name | string | The name given to the price listing set.
created-at | datetime | Date of the price listing set's creation.
updated-at | datetime | Date of the last price listing set's update.

### Include

* `price-listings`: All the <a href="#price-listings">price listings</a> included in this price listing set.
* `tutor-profile`: The <a href="#tutor-profiles">tutor profile</a> associated to this price listing set.

## Create a price listing set

###### <verb class="post">POST</verb> /api/v1/__price-listing-sets__

This endpoint adds a new price listing to a competence or to a price listing set (one or the other is required).

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
name | string | The name given to the price listing set.


## Update a price listing set

###### <verb class="put">PUT</verb> /api/v1/__price-listing-sets/:id__

This endpoint allows to update a given price listing set. 

<aside class="notice">
Users can only update their own price listing sets, unless they are granted a <code>price-listing-sets.update</code> role.
</aside>

### Parameters

Attributes | Type | Description
---------- | ---- | -----------
name | string | The name given to the price listing set.


## Delete a price listing set

###### <verb class="delete">DELETE</verb> /api/v1/__price-listing-sets/:id__

This endpoint allows to delete a given price listing set. 

<aside class="notice">
Users can only delete their own price listing sets, unless they are granted a <code>price-listing-sets.destroy</code> role.
</aside>
