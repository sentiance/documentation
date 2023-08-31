# VehicleCrashEvent

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

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

