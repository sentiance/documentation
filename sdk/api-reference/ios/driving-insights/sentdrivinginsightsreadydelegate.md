# SENTDrivingInsightsReadyDelegate

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

This delegate is used to set  [`drivingInsightsProcessedDelegate`](../sentiance.md#drivinginsightsprocesseddelegate).

```objectivec
SWIFT_PROTOCOL_NAMED("DrivingInsightsReadyDelegate")
@protocol SENTDrivingInsightsReadyDelegate
```

## SENTDrivingInsightsReadyDelegate API

### `onDrivingInsightsReadyWithInsights`

> Invoked when driving insights become available for a transport.
>
> ```objectivec
> - (void)onDrivingInsightsReadyWithInsights:(SENTDrivingInsights * _Nonnull)insights;
> ```
