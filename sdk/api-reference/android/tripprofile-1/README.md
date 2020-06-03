# TripProfileConfig

This class allows you to control how the SDK should profile trips, i.e. on-device or via the Sentiance platform. It uses the builder pattern to provide additional options related to profiling trips on-device.

## TripProfileConfig API

|  |  |
| :--- | :--- |
| Double | [getSpeedLimit](./#getspeedlimit) \(\) |
| boolean | [isFullProfilingEnabled](./#isfullprofilingenabled) \(\) |



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

