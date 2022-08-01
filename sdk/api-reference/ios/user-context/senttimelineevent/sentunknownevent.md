# SENTUnknownEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTUnknownEvent : SENTTimelineEvent <NSSecureCoding>

- (BOOL)isEqualToUnknownEvent:(SENTUnknownEvent *)unknownEvent;

@end
```
