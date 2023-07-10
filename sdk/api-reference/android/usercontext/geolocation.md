# GeoLocation

Represents a geographic location.

## GeoLocation API

|         |                                                              |
| ------- | ------------------------------------------------------------ |
| int     | [getAccuracyInMeters](geolocation.md#getaccuracyinmeters) () |
| double  | [getLatitude](geolocation.md#getlatitude) ()                 |
| double  | [getLongitude](geolocation.md#getlongitude) ()               |
| boolean | [hasAccuracy](geolocation.md#hasaccuracy) ()                 |



### `getAccuracyInMeters()`

> ```java
> int getAccuracyInMeters()
> ```
>
> Returns the accuracy in meters.
>
> If this location does not have an accuracy, then -1 is returned.

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

### hasAccuracy`()`

> ```java
> boolean hasAccuracy()
> ```
>
> Returns `true` if this location has a horizontal accuracy, `false` otherwise.
