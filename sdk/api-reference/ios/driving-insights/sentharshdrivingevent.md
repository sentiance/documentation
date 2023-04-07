# SENTHarshDrivingEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
SWIFT_CLASS_NAMED("HarshDrivingEvent")
@interface SENTHarshDrivingEvent : NSObject
```

## SENTDrivingInsights API

### `date`

> Returns the date and time of occurrence of the event.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTDate * _Nonnull date;
> ```

### `magnitude`

> Returns the magnitude of the harsh event, in m/s^2.
>
> ```objectivec
> @property (nonatomic, readonly) float magnitude;
> ```
