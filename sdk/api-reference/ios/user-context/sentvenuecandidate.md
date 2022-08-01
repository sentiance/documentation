---
description: >-
  Represents a venue the user was likely at, with a corresponding likelihood,
  and a list of historic visits to this venue.
---

# SENTVenueCandidate

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
@interface SENTVenueCandidate : NSObject <NSSecureCoding, NSCopying>
```

### venue

The venue information where the user was likely at.

```
@property (nonatomic, strong, nonnull, readonly) SENTVenue *venue;
```



### likelihood

Returns the likelihood of the user being at this venue, having a value between 0 and 1, where 1 represents extreme likelihood.

```
@property (nonatomic, assign, readonly) Float32 likelihood;
```



### visits

History of visits to this venue.

```
@property (nonatomic, strong, nonnull, readonly) NSArray<SENTVisit *> *visits;
```



### initWithVenue: likelihood: visits

```
- (instancetype)initWithVenue:(SENTVenue *)venue likelihood:(Float32)likelihood visits:(NSArray *)visits;
```



### isEqualToVenueCandidate:

```
- (BOOL)isEqualToVenueCandidate:(SENTVenueCandidate *)venueCandidate;
```
