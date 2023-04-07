# SENTDrivingInsights

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
SWIFT_CLASS_NAMED("DrivingInsights")
@interface SENTDrivingInsights : NSObject
```

## SENTDrivingInsights API

### `transportEvent`

> Returns the [transport event](../user-context/senttimelineevent/senttransportevent.md).
>
> <pre class="language-objectivec"><code class="lang-objectivec"><strong>@property (nonatomic, readonly, strong) SENTTransportEvent * _Nonnull transportEvent;
> </strong></code></pre>

### `safetyScores`

> Returns the [safety scores](sentsafetyscores.md).
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTSafetyScores * _Nonnull safetyScores;
> ```
