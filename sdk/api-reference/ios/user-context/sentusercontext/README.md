---
description: Represents the user's context during a specific moment in time.
---

# SENTUserContext

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

The context includes:

* a list of recent events, such as stationaries and transports;
* the user's active moments and segments at the time this context was constructed;
* the user's home and work locations;
* the user's last know location, if SDK detections were running.



### events

Returns a list of recent events, composed of stationaries, transports, and off-the-grids.

The list is ordered from the most recent event to the oldest one, and includes the last detected event at the time this context was constructed, plus all preceding events up until the last stationary or off-the-grid.

```
@property (nonatomic, strong, nonnull) NSArray<SENTTimelineEvent *> *events;
```

###

### activeMoments

Returns the active moments detected for the user at the time this context was constructed.

```
@property (nonatomic, strong, nonnull) NSArray<SENTMoment *> *activeMoments;
```



### activeSegments

Returns the active segments detected for the user at the time this context was constructed.

```
@property (nonatomic, strong, nonnull) NSArray<SENTSegment *> *activeSegments;
```



### lastKnownLocation

Returns the user's last known location at the time this context was constructed. If the user's last detected event was off-the-grid, or no location information was available, nil is returned instead.

```
@property (nonatomic, strong, nullable) SENTGeolocation *lastKnownLocation;
```



### home

Returns the user's home location if known, otherwise returns nil.

```
@property (nonatomic, strong, nullable) SENTVenue *home;
```

###

### work

Returns the user's work location if known, otherwise returns nil.

```
@property (nonatomic, strong, nullable) SENTVenue *work
```



### isEqualToUserContext:

```
- (BOOL)isEqualToUserContext:(SENTUserContext *)userContext;
```
