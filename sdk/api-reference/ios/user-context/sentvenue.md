---
description: Represents a place of interest.
---

# SENTVenue

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
@interface SENTVenue : NSObject <NSSecureCoding, NSCopying>
```

### location

Returns the location of the venue, as [SENTGeolocation](sentgeolocation.md), if known. Otherwise returns nil. For example, this value will be nil if the venue significance is "point of interest."

```objectivec
@property (nonatomic, strong, nullable, readonly) SENTGeolocation *location;
```

### significance

Returns the significance of the venue (i.e. home, work, or a point of interest), as [SENTVenueSignificance](sentvenuesignificance.md).

```objectivec
@property (nonatomic, assign, readonly) SENTVenueSignificance significance;
```

### venueType

Returns the type of the venue, as [SENTVenueType](sentvenuetype.md).

```objectivec
@property (nonatomic, assign, readonly) SENTVenueType type;
```

### isEqualToVenue:

```objectivec
- (BOOL)isEqualToVenue:(SENTVenue *)venue;
```
