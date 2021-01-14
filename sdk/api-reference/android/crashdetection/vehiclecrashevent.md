# VehicleCrashEvent

Represents a vehicle crash event detected by the Sentiance SDK.

## VehicleCrashEvent API

|  |  |
| :--- | :--- |
| Integer | [getConfidence](vehiclecrashevent.md#getconfidence) \(\) |
| Float | [getDeltaV](vehiclecrashevent.md#getdeltav) \(\) |
| [Location](https://developer.android.com/reference/android/location/Location) | [getLocation](vehiclecrashevent.md#getlocation) \(\) |
| Float | [getMagnitude](vehiclecrashevent.md#getmagnitude) \(\) |
| Float | [getSpeedAtImpact](vehiclecrashevent.md#getspeedatimpact) \(\) |
| long | [getTime](vehiclecrashevent.md#gettime) \(\) |



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



