# Waypoint

Represents a geographic location

## Waypoint API

<table data-header-hidden><thead><tr><th width="206"></th><th></th></tr></thead><tbody><tr><td>double</td><td><a href="transportevent.md#getlatitude">getLatitude</a> ()</td></tr><tr><td>double</td><td><a href="transportevent.md#getlongitude">getLongitude</a> ()</td></tr><tr><td>int</td><td><a href="transportevent.md#getaccuracyinmeters">getAccuracyInMeters</a> ()</td></tr><tr><td>boolean</td><td><a href="transportevent.md#hasaccuracy">hasAccuracy</a> ()</td></tr><tr><td>long</td><td><a href="transportevent.md#gettimestamp">getTimestamp</a> ()</td></tr></tbody></table>



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
