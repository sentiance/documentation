# StationaryEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a duration of time when the user was stationary.

## StationaryEvent API

|                                                    |                                                                |
| -------------------------------------------------- | -------------------------------------------------------------- |
| [EventType](eventtype.md)                          | [getEventType](stationaryevent.md#geteventtype) ()             |
| [GeoLocation](../geolocation.md)                   | [getLocation](stationaryevent.md#getlocation) ()               |
| List<[VenueCandidate](../venue/venuecandidate.md)> | [getVenueCandidates](stationaryevent.md#getvenuecandidates) () |
| [VenueType](../venue/venuetype.md)                 | [getVenueType](stationaryevent.md#getvenuetype) ()             |



### `getEventType()`

> ```java
> EventType getEventType()
> ```
>
> Returns the type of this event.

### `getLocation()`

> ```java
> GeoLocation getLocation()
> ```
>
> Returns the location where the user is stationary at.

### `getVenueCandidates()`

> ```java
> List<VenueCandidate> getVenueCandidates()
> ```
>
> Returns a list of likely venues the user is stationary at.

### `getVenueType()`

> ```java
> VenueType getVenueType()
> ```
>
> Returns the type of venue the user is stationary at.
