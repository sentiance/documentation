# SENTMoment

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTMoment : NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) SENTMomentType type;
@property (nonatomic, strong, nonnull) SENTDate *startDate;
@property (nonatomic, strong, nullable) SENTDate *endDate;
@property (nonatomic, strong, nonnull) NSArray<SENTAttribute *> *attributes;

- (BOOL)isEqualToMoment:(SENTMoment *)moment;

@end
```
