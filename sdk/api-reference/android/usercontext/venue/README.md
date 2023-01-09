# Venue

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a place of interest.

## Venue API

### `getLocation()`

> ```java
> @Nullable GeoLocation getLocation()
> ```
>
> Returns the location of the venue, as [GeoLocation](../geolocation.md), if known. Otherwise returns null.

### `getSignificance()`

> ```java
> VenueSignificance getSignificance()
> ```
>
> Returns the significance of the venue (i.e. home, work, or a point of interest), as [VenueSignificance](segmenttype.md).

### getType`()`

> ```java
> VenueType getType()
> ```
>
> Returns the type of the venue, as [VenueType](venuetype.md).
