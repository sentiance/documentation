# UserActivity

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Represents a user activity detected by the SDK detections.

## UserActivity API

### `getActivityType()`

> ```java
> UserActivityType getActivityType()
> ```
>
> Returns a [`UserActivityType`](useractivitytype.md) enum representing the detected activity type.

### `getTripInfo()`

> ```java
> @Nullable TripInfo getTripInfo()
> ```
>
> Returns a [`TripInfo`](tripinfo.md) object containing info about the ongoing trip. If the current activity is not a trip, this method will return `null` instead.

### `getStationaryInfo()`

> ```java
> @Nullable StationaryInfo getStationaryInfo()
> ```
>
> Returns a [`StationaryInfo`](stationaryinfo.md) object containing info about the current stationary state. If the current activity is not a stationary, this method will return `null` instead.
