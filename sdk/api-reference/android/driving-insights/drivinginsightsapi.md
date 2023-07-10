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

<table><thead><tr><th width="243">Parameters</th><th></th></tr></thead><tbody><tr><td>transportId</td><td>The ID of the desired transport.</td></tr></tbody></table>

### `getHarshDrivingEvents()`

> ```java
> List<HarshDrivingEvent> getHarshDrivingEvents(String transportId)
> ```
>
> Returns the [harsh driving events](harshdrivingevent.md) for a completed transport.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

<table><thead><tr><th width="244">Parameters</th><th></th></tr></thead><tbody><tr><td>transportId</td><td>The ID of the desired transport.</td></tr></tbody></table>

### `getPhoneUsageEvents()`

> ```java
> List<PhoneUsageEvent> getPhoneUsageEvents(String transportId)
> ```
>
> Returns the [phone usage events](phoneusageevent.md) for a completed transport.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

<table><thead><tr><th width="244">Parameters</th><th></th></tr></thead><tbody><tr><td>transportId</td><td>The ID of the desired transport.</td></tr></tbody></table>

### `setDrivingInsightsReadyListener()`

> ```java
> void setDrivingInsightsReadyListener(@Nullable DrivingInsightsReadyListener listener)
> ```
>
> Sets a listener that will be invoked when the driving insights for a completed transport becomes ready.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

<table><thead><tr><th width="248">Parameters</th><th></th></tr></thead><tbody><tr><td>listener</td><td>A <a href="drivinginsightsreadylistener.md"><code>DrivingInsightsReadyListener</code></a> to receive the driving insights. Set <code>null</code> to remove a previously set listener.</td></tr></tbody></table>



