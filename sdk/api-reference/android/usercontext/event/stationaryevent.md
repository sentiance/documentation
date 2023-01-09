# StationaryEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a duration of time when the user was stationary.

## StationaryEvent API

|                                  |                                                    |
| -------------------------------- | -------------------------------------------------- |
| [EventType](eventtype.md)        | [getEventType](stationaryevent.md#geteventtype) () |
| [GeoLocation](../geolocation.md) | [getLocation](stationaryevent.md#getlocation) ()   |
| [Venue](../venue/)               | [getVenue](stationaryevent.md#getvenuetype) ()     |



### `getEventType()`

> ```java
> EventType getEventType()
> ```
>
> Returns the type of this event.

### `getLocation()`

> ```java
> @Nullable GeoLocation getLocation()
> ```
>
> Returns the location where the user is stationary at.

### `getVenue()`

> ```java
> Venue getVenue()
> ```
>
> Returns the venue of this stationary.
