# VehicleCrashEvent

Represents a vehicle crash event detected by the Sentiance SDK.

## VehicleCrashEvent API

### `getConfidence()`

> ```java
> @Nullable Integer getConfidence()
> ```
>
> Returns a confidence value between 0 and 100.

### `getDeltaV()`

> ```java
> @Nullable Float getDeltaV()
> ```
>
> Returns the delta-v estimated over the peak duration, in meter per second.

### `getLocation()`

> ```java
> @Nullable Location getLocation()
> ```
>
> Returns the last known location prior to the crash.

### `getMagnitude()`

> ```java
> @Nullable Float getMagnitude()
> ```
>
> Returns the magnitude of the crash event in meter per second squared.

### `getPrecedingLocations()`

> ```java
> List<Location> getPrecedingLocations()
> ```
>
> Returns a list of recent locations (from the oldest to the most recent) leading up to this crash, within a certain timeframe.

### `getSpeedAtImpact()`

> ```java
> @Nullable Float getSpeedAtImpact()
> ```
>
> Returns the inferred speed at the moment of impact, in meter per second.

### `getTime()`

> ```java
> long getTime()
> ```
>
> Returns the UTC time of the crash event in milliseconds.

