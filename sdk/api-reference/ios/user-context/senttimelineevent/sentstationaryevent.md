---
description: Represents a duration of time when the user was stationary.
---

# SENTStationaryEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
@interface SENTStationaryEvent : SENTTimelineEvent <NSSecureCoding>
```

### location

Location where the user is stationary at. nil only when timeline data is missing.

```
@property (nonatomic, strong, nullable, readonly) SENTGeolocation *location;
```

### venue

The venue where the user is stationary at.

```
@property (nonatomic, strong, readonly) SENTVenue *venue;
```

### isEqualToStationaryEvent:

```
- (BOOL)isEqualToStationaryEvent:(SENTStationaryEvent *)stationaryEvent;
```

