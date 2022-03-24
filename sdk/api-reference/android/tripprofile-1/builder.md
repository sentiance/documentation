# Builder

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v4.21.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

This class is used with [`updateTripProfileConfig(TripProfileConfig)`](../sentiance.md#updatetripprofileconfig).

## Builder API

### `setSpeedLimit()`

> ```java
> public Builder setSpeedLimit(@Nullable Double speedLimit)
> ```
>
> Sets the speed limit in km/h, which is used to determine the percent of time the user was speeding. If null, the SDK will use an internal default value.

| Parameters |                          |
| ---------- | ------------------------ |
| speedLimit | The speed limit in km/h. |

### `enableFullProfiling()`

> ```java
> public Builder enableFullProfiling(boolean enabled)
> ```
>
> Switches the trip profiling mode between full and on-device profiling. If set to true, full trip profiling will be enabled allowing the Sentiance platform to profile the trip and the results made available via the API. In addition, the app will no longer receive trip profiles via the [`TripProfileListener`](../tripprofilelistener.md) set with [`setTripProfileListener(TripProfileListener)`](../sentiance.md#settripprofilelistener).

| Parameters |                                                                         |
| ---------- | ----------------------------------------------------------------------- |
| enabled    | `true` to enable full profiling. `false` to enable on-device profiling. |
