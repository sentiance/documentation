---
description: Represents a duration of the time when the user was in transport.
---

# SENTTransportEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
@interface SENTTransportEvent : SENTTimelineEvent <NSSecureCoding>
```

### transportMode

Returns the mode of transportation.

```
@property (nonatomic, assign) SENTTimelineTransportMode transportMode;
```



### isEqualToTransportEvent:

```
- (BOOL)isEqualToTransportEvent:(SENTTransportEvent *)transportEvent;
```
