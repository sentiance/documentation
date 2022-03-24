# TripProfileConfig

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v4.21.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

This class allows you to control how the SDK should profile trips, i.e. on-device or via the Sentiance platform. It uses the builder pattern to provide additional options related to profiling trips on-device.

## TripProfileConfig API

### `getSpeedLimit()`

> ```java
> public Double getSpeedLimit()
> ```
>
> Returns the speed limit set by the app. Null is returned if the app never set the speed limit.

### `isFullProfilingEnabled()`

> ```java
> public boolean isFullProfilingEnabled()
> ```
>
> Returns true if the app set the profiling mode to true, otherwise returns false.
