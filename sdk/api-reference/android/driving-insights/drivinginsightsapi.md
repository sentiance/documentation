# DrivingInsightsApi

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Use this API to receive driving insights about vehicular transports.

## DrivingInsightsApi API

### `getDrivingInsights()`

> ```java
> @Nullable DrivingInsights getDrivingInsights(String transportId)
> ```
>
> Returns the [driving insights](drivinginsights.md) for a given transport, or `null` if there are no driving insights or the transport ID is invalid.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

| Parameters  |                                  |
| ----------- | -------------------------------- |
| transportId | The ID of the desired transport. |

### `getHarshDrivingEvents()`

> ```java
> List<HarshDrivingEvent> getHarshDrivingEvents(String transportId)
> ```
>
> Returns the [harsh driving events](harshdrivingevent.md) for a completed transport.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

| Parameters  |                                  |
| ----------- | -------------------------------- |
| transportId | The ID of the desired transport. |

### `setDrivingInsightsReadyListener()`

> ```java
> void setDrivingInsightsReadyListener(@Nullable DrivingInsightsReadyListener listener)
> ```
>
> Sets a listener that will be invoked when the driving insights for a completed transport becomes ready.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

| Parameters |                                                                                                                                                      |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| listener   | A [`DrivingInsightsReadyListener`](drivinginsightsreadylistener.md) to receive the driving insights. Set `null` to remove a previously set listener. |



