# UserActivity

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
