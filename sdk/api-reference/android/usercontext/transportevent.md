# Waypoint

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a geographic location

## Waypoint API

| double  | [getLatitude](transportevent.md#getlatitude) ()                 |
| ------- | --------------------------------------------------------------- |
| double  | [getLongitude](transportevent.md#getlongitude) ()               |
| int     | [getAccuracyInMeters](transportevent.md#getaccuracyinmeters) () |
| boolean | [hasAccuracy](transportevent.md#hasaccuracy) ()                 |
| long    | [getTimestamp](transportevent.md#gettimestamp) ()               |



### `getLatitude()`

> ```java
> double getLatitude()
> ```
>
> Returns the latitude in degrees.

### `getLongitude()`

> ```java
> double getLongitude()
> ```
>
> Returns the longitude in degrees.

### getAccuracyInMeters`()`

> ```java
> int getAccuracyInMeters()
> ```
>
> Returns the accuracy in meters.
>
> If this location does not have an accuracy, then -1 is returned.

### hasAccuracy`()`

> ```java
> boolean hasAccuracy()
> ```
>
> Returns `true` if this location has a horizontal accuracy, `false` otherwise.

### getTimestamp`()`

> ```java
> long getTimestamp()
> ```
>
> Return the UTC time of this waypoint, in milliseconds since epoch (January 1, 1970).
