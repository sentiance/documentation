# SENTSemanticTime

{% hint style="info" %}
This type is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Enum representation of the semantic time.

```
typedef NS_ENUM(NSUInteger, SENTSemanticTime) {
    SENTSemanticTimeUnknown = 0,
    SENTSemanticTimeMorning,
    SENTSemanticTimeLateMorning,
    SENTSemanticTimeLunch,
    SENTSemanticTimeAfternoon,
    SENTSemanticTimeEarlyEvening,
    SENTSemanticTimeEvening,
    SENTSemanticTimeNight,
};
```
