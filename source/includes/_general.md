# General

## Time zones

Time zones are represented by friendly names that map to <a target="_blank" href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">tz database names</a>. 
For example, an API request returns "Eastern Time (US & Canada)" instead of "America/New_York". 
You can map the friendly names to the tz database names by referencing the Constants > Mapping 
section of the Ruby on Rails <a target="_blank" href="http://api.rubyonrails.org/classes/ActiveSupport/TimeZone.html">TimeZone object doc</a>.

## Phone Number

The phone number should comply with the E.164 international telephone numbering plan. 

Example +1 555-123-4567. E164 numbers are international numbers with a country dial prefix, 
usually an area code and a subscriber number.

A valid E.164 phone number must include a country calling code.

## Country code

Tutory uses the <a href="https://www.iso.org/iso-3166-country-codes.html">ISO 3166-1</a> country codes standard to name countries and ISO 3166-2 subdivisions. 

Example 

English name | Alpha-2 code | Alpha-3 code | Numeric code | Subdivision code (ISO_3166-2)
------------ | ----------- | ------------ | ------------ | -----------------------------
Australia | AU | AUS | 036 | ISO_3166-2:AU
France | FR | FRA | 250 | 	ISO 3166-2:FR


Code | Subdivision name (en) | Subdivision category
---- | --------------------- | ---------------------
AU-NSW | New South Wales | state
AU-VIC | Victoria | state
AU-ACT | Australian Capital Territory | territory
FR-NOR | Normandie | region
FR-IDF | Île-de-France | region

## Gender code

Tutory follows the vCard4 standard as it has the most up to date, modern, and inclusive notion of "gender".

* F = female,
* M = male,
* O = other,
* N = none or not applicable,
* U = unknown
