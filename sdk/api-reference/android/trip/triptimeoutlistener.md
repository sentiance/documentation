# TripTimeoutListener

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`setTripTimeoutListener(TripTimeoutListener)`](../sentiance.md#settriptimeoutlistener).

## TripTimeoutListener API

### `onTripTimeout()`

> ```java
> void onTripTimeout()
> ```
>
> Called when a trip has exceeded the maximum duration.
>
> This is only used when [triggered trips](../../../appendix/controlled-detections/controlled-trips-only.md) is enabled in the [`SdkConfig`](../sdkconfig/).
