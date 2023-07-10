---
description: Represents a duration of time when the user was stationary.
---

# SENTStationaryEvent

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

