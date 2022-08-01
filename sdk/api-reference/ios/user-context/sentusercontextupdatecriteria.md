# SENTUserContextUpdateCriteria

{% hint style="info" %}
This type is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
typedef NS_OPTIONS(NSUInteger, SENTUserContextUpdateCriteria)
```

| Type                                            | Description                                      |
| ----------------------------------------------- | ------------------------------------------------ |
| **SENTUserContextUpdateCriteriaCurrentEvent**   | A change in the user's current or ongoing event. |
| **SENTUserContextUpdateCriteriaActiveMoments**  | A change in the user's active moments.           |
| **SENTUserContextUpdateCriteriaActiveSegments** | A change in the user's active segments.          |
| **SENTUserContextUpdateCriteriaVisitedVenues**  | A change in the user's visited venues.           |
| **SENTUserContextUpdateCriteriaAll**            | All criteria applied.                            |

##
