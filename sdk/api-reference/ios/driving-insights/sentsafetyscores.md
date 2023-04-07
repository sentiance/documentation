# SENTSafetyScores

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTSafetyScores : NSObject
```

## SENTDrivingInsights API

### `smoothScore`

> Returns smooth driving score, which is between 0 and 1, where 1 is the perfect score.
>
> ```objectivec
> @property (nonatomic, strong, nullable) NSNumber *smoothScore;
> ```
