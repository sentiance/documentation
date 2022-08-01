---
description: Visit to a particular venue.
---

# SENTVisit

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

### startDate

Returns the start time of the visit.

```
@property (nonatomic, strong, nonnull) SENTDate *startDate;
```



### endDate

Returns the end time of the visit.

```
@property (nonatomic, strong, nonnull) SENTDate *endDate;
```

###

### durationInSeconds

Returns the duration of the visit, in seconds.

```
@property (nonatomic, assign) NSInteger durationInSeconds;
```

###

### isEqualToVisit:

```
- (BOOL)isEqualToVisit:(SENTVisit *)visit;
```

