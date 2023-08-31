# StationaryInfo

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Provides information about a stationary.

## StationaryInfo API

### `getLocation()`

> ```java
> Location getLocation()
> ```
>
> Returns a [`Location`](https://developer.android.com/reference/android/location/Location) object representing the stationary location.

### `getPointsOfInterest()`

> ```java
> List<PointOfInterest> getPointsOfInterest()
> ```
>
> Returns a list of [`PointOfInterest`](pointofinterest.md) objects representing the points of interest near the user's stationary location.
