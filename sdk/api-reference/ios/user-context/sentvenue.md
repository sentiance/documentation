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



### name

Returns the name of the venue if available. Otherwise, returns nil.

```
@property (nonatomic, copy, nullable) NSString *name;
```

### location

Returns the location of the venue.

```
@property (nonatomic, strong, nonnull) SENTGeolocation *location;
```

### labels

Returns a map of labels assigned to the venue.

{% hint style="warning" %}
Note: due to ongoing development, the contents of this mapping are subject to change.
{% endhint %}

```
@property (nonatomic, strong, nonnull) NSDictionary<NSString *, NSString *> *labels;
```



### isEqualToVenue:

```
- (BOOL)isEqualToVenue:(SENTVenue *)venue;
```
