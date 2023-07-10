# SENTPhoneUsageEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
SWIFT_CLASS_NAMED("PhoneUsageEvent")
@interface SENTPhoneUsageEvent : SENTDrivingEvent
```

## SENTPhoneUsageEvent API

### `startDate`

> The start date of the event.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTDate * _Nonnull startDate;
> ```

### `endDate`

> The end date of the event.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTDate * _Nonnull endDate;
> ```
