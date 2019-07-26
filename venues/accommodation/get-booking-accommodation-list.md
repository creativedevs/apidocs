# Get Booking Accommodation List

{% api-method method="post" host="\[PlatformAddress\]/api/1.0/venue?action=getBookingAccommodationList" path="" %}
{% api-method-summary %}
Get Booking Accommodation List
{% endapi-method-summary %}

{% api-method-description %}
Get a list of booking accommodation \(i.e. groups\) for a specific venue booking.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="venueId" type="integer" required=true %}
The unique id of the venue to which the bookings belong
{% endapi-method-parameter %}

{% api-method-parameter name="bookingId" type="integer" required=true %}
The unique id of the booking to which the accommodation belongs
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "meta": {
        "totalResults": 5,
        "start": 0,
        "perPage": 5,
        "count": 5
    },
    "results": [{
        "id": 1432,
        "venueId": 178,
        "bookingId": 4304,
        "roomVenueId": 178,
        "barId": null,
        "roomId": 76,
        "startDate": "2018-08-27",
        "endDate": "2018-08-31",
        "overrideCapacity": true,
        "costcenterId": 1376,
        "cutOffDate": "2018-08-15",
        "dayRates": [
            {
                "bookingDate": "2018-08-27",
                "numRooms": 11,
                "cost": 180,
                "numPayableByGuest": 11,
                "numFreeRooms": 1
            },
            {
                "bookingDate": "2018-08-28",
                "numRooms": 12,
                "cost": 190,
                "numPayableByGuest": 12,
                "numFreeRooms": 1
            },
            {
                "bookingDate": "2018-08-29",
                "numRooms": 13,
                "cost": 175,
                "numPayableByGuest": 13,
                "numFreeRooms": 1
            },
            {
                "bookingDate": "2018-08-30",
                "numRooms": 14,
                "cost": 210,
                "numPayableByGuest": 14,
                "numFreeRooms": 1
            }
        ],
        "excludedTaxIds": [],
        "roomOptions": [
            {
                "bookingDate": "2018-08-27",
                "roomOptionId": 35,
                "numRooms": 11,
                "numOptionsPerRoom": 1,
                "price": 65,
                "excludedTaxIds": [],
                "totalAmount": 715,
                "totalTaxAmount": 65.01,
                "costcenterId": 1377,
                "numPayableByGuest": 11
            },
            {
                "bookingDate": "2018-08-30",
                "roomOptionId": 36,
                "numRooms": 10,
                "numOptionsPerRoom": 1,
                "price": 80,
                "excludedTaxIds": [],
                "totalAmount": 800,
                "totalTaxAmount": 72.7,
                "costcenterId": 1377,
                "numPayableByGuest": 10
            }
        ],
        "createdDate": "2018-08-22 06:43:24 UTC",
        "modifiedDate": "2018-08-22 06:43:24 UTC"
    }]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

The result from this call will be a [collection](../../getting-started/interpreting-the-response/collections.md) of booking accomodation records the user has access to. This call returns all accommodation records for a specific venue booking - it does not accept [pagination](../../getting-started/interpreting-the-response/pagination.md) or [filter](../../getting-started/interpreting-the-response/filtering.md) properties.

## Booking Accommodation \(Group\)

| Property | Type | Description |
| :--- | :--- | :--- |
| id | integer | The unique id of the booking accommodation |
| venueId | integer | The unique id of the venue to which the booking belongs |
| bookingId | integer | The unique id of the booking to which the accommodation group belongs |
| roomVenueId | integer | The unique id of the venue to which the rate plan \(barId\) and room type \(roomId\) belong \(can be different to venueId\) |
| barId | integer | The unique id of the rate plan assigned to the accommodation group |
| roomId | integer | The unique id of the room type assigned to the accommodation group |
| startDate | date | The arrival date of the accommodation group |
| endDate | date | The departure date of the accommodation group |
| overrideCapacity | boolean | Whether or not the accommodation group can exceed the general room availability |
| costcenterId | integer | The unique id of the cost center assigned to the accommodation group |
| cutOffDate | date | The date after which changes to the accommodation group are not allowed |
| dayRates | array of [Day Rates](get-booking-accommodation-list.md#booking-accommodation-day-rates) | The daily rates of the accommodation group |
| excludedTaxIds | array of integers | The unique ids of the taxes that are excluded from the daily rates |
| roomOptions | array of [Room Options](get-booking-accommodation-list.md#booking-accommodation-room-option) | The additional room options of the accommodation group |
| createdDate | datetime | The date & time the accommodation group was created |
| modifiedDate | datetime | The date & time the acommodation group was last modified |

## Booking Accommodation Day Rates

| Property | Type | Description |
| :--- | :--- | :--- |
| bookingDate | date | The date of the accommodation group to which the rate applies |
| numRooms | integer | The number of rooms booked on bookingDate |
| cost | number | The rate amount for the room on bookingDate. The amount either includes or excludes tax depending on how the venue is configured |
| numPayableByGuest | integer | The number of rooms on bookingDate that are payable by guests \(as opposed to the master account of the booking\) |
| numFreeRooms | integer | The number of complimentary \(free\) rooms on bookingDate. This number is included in numRooms |

## Booking Accommodation Room Option

| Property | Type | Description |
| :--- | :--- | :--- |
| bookingDate | date | The date of the accommodation group to which the additional option applies |
| roomOptionId | integer | The unique id of the room option added on bookingDate |
| numRooms | integer | The number of rooms on bookingDate to which the room option applies |
| numOptionsPerRoom | integer | The number options added to each room \(numRooms\) on bookingDate |
| price | number | The price of the additional option. The amount either includes or excludes tax depending on how the venue is configured |
| excludedTaxIds | array of integers | The unique ids of the taxes that are excluded from price |
| totalAmount | number | The total value of the additional option on this date, including all applicable taxes |
| totalTaxAmount | number | The total tax amount included in totalAmount |
| costcenterId | integer | The unique id of the cost center assigned to the additional option |
| numPayableByGuest | integer | The number of additional options on bookingDate that are payable by guests \(as opposed to the master account of the booking\) |

