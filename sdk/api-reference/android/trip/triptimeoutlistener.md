# TripTimeoutListener

This interface is used with [`setTripTimeoutListener(TripTimeoutListener)`](../sentiance.md#settriptimeoutlistener).

## TripTimeoutListener API

|  |  |
| :--- | :--- |
| void | [onTripTimeout](triptimeoutlistener.md#ontriptimeout) \(\) |



### `onTripTimeout()`

> ```java
> void onTripTimeout()
> ```
>
> Called when a trip has exceeded the maximum duration.
>
> This is only used when [triggered trips](../../../appendix/controlled-detections/controlled-trips-only.md) is enabled in the [`SdkConfig`](../sdkconfig/).

