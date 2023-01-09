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

### distanceInMeters

Returns the distance travelled during the transport, in meters. If distance cannot be computed, then returns nil.

```objectivec
@property (nonatomic, strong, readonly, nullable) NSNumber *distanceInMeters NS_REFINED_FOR_SWIFT;
```

### transportMode

Returns the mode of transportation as [SENTTimelineTransportMode](../senttimelinetransportmode.md).

```
@property (nonatomic, assign) SENTTimelineTransportMode transportMode;
```

### waypoints

Returns the waypoints collected during the transport.

```objectivec
@property (nonatomic, strong, readonly) NSArray<SENTWaypoint *> *waypoints;
```

### isEqualToTransportEvent:

```objectivec
- (BOOL)isEqualToTransportEvent:(SENTTransportEvent *)transportEvent;
```
