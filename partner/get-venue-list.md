---
description: 'NOTE: This action has not been published yet.'
---

# Get Venue List

{% api-method method="post" host="\[PlatformAddress\]" path="/api/1.0/partner?action=getVenueList" %}
{% api-method-summary %}
Get Venue List
{% endapi-method-summary %}

{% api-method-description %}
Fetch a list of venues that are visible in the marketplace.The result from this call will be a collection of all the venues visible in the marketplace matching the request criteria below. This call also accepts the pagination properties.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="availabilityStartDate" type="date" required=false %}
The start date of the period from which to include the function space availability details of the venues
{% endapi-method-parameter %}

{% api-method-parameter name="availabilityEndDate" type="date" required=false %}
The end date of the period from which to include the function space availability details of the venues
{% endapi-method-parameter %}

{% api-method-parameter name="allowsLiveBook" type="boolean" required=false %}
Use this to filter venues that do, or do not, allow live bookings
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalResults": 1,
    "start": 0,
    "perPage": 100,
    "count": 1
  },
  "results": [
    {
      "id": 21,
      "hashId": "1efda3e35a75aabd13e8996037d35a79",
      "businessName": "iVvy Conference Centre",
      "businessNumber": 123123,
      "phone": "1300 004 889",
      "fax": "",
      "websiteAddress": "",
      "emailAddress": "example@domain.com",
      "description": "<p>Located by the River at Hamilton, this is the closest 5 star, full service Hotel to the Brisbane Cruise Terminal - Portside at Hamilton, the Airport precinct, Gateway Arterial Bridge linking the Gold Coast to the Sunshine Coast and is just minutes from the CBD.<br /><br />  Featuring 90 spacious, newly refurbished and well appointed accommodation rooms, the hotel is an urban escape perfect for business or leisure travellers alike. Most rooms feature magnificent views of the widest reach of the Brisbane River spanning from the Brisbane City past the Brisbane Cruise Terminal and to the Gateway Bridge.<br /><br />  Enjoy the resort style pool, spa, sauna, gym and complimentary car parking &amp; Wi-Fi for all delegates, guests and visitors.<br /><br />  From the grandeur of the column free Hamilton Ballroom which can easily divide into smaller configurations, the intimacy of the Newstead Room or take advantage of the newly refurbished Executive Boardroom the Brisbane Riverview Hotel has an option to suit your budget and requirements. The resort style pool area is a fantastic venue for breakout sessions or lunches. This is a flexible and well equipped conference venue can cater for intimte boardroom meeting of 6 people up to large corporate events for up to 300 delegates. <br /><br />  With expansive river views, Plates Restaurant offers a seasonal menu showcasing superb produce from Queensland&#8217;s freshest seafood, international cuisine, and wood fired steaks and pizzas. It is the perfect place for business or pleasure, mixing excellent atmosphere with great service.</p>",
      "checkinTime": "11:00:00",
      "checkoutTime": "14:00:00",
      "childAge": 0,
      "infantAge": 0,
      "currencyCode": "AUD",
      "localeCode": "en_AU",
      "timezone": "Australia/Brisbane",
      "hasSpaces": true,
      "hasAccommodation": true,
      "numMeetingRooms": 0,
      "numAccommodationRooms": 200,
      "maxSpaceArea": null,
      "totalSpaceArea": null,
      "longitude": "153.4065773",
      "latitude": "-28.0067947",
      "primaryAddress": {
        "line1": "2 Boston Court",
        "line2": "",
        "line3": "",
        "line4": "",
        "city": "Varsity Lakes",
        "stateCode": "QLD",
        "stateName": null,
        "countryCode": "AU",
        "countryName": null,
        "postalCode": 4227
      },
      "isTaxExclusive": false,
      "allowsLiveBook": true,
      "instantBookUrl": "http://stagemarketplace.ivvy.com/order/start?v=1efda3e35a75aabd13e8996037d35a79",
      "availability": {
        "2015-05-20": {
          "isAvailable": true
        },
        "2015-05-21": {
          "isAvailable": true
        },
        "2015-05-22": {
          "isAvailable": true
        },
        "2015-05-23": {
          "isAvailable": true
        },
        "2015-05-24": {
          "isAvailable": true
        },
        "2015-05-25": {
          "isAvailable": true
        },
        "2015-05-26": {
          "isAvailable": true
        }
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example Request

Example: Fetch the 2nd batch of 100 venues visible in the marketplace. Include their availability from 1st July 2015 to 7th July 2015

```javascript
{
  "start": 100,
  "availabilityStartDate": "2015-07-01",
  "availabilityEndDate": "2015-07-07"
}
```

