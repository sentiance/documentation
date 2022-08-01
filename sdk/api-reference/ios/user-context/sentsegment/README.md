# SENTSegment

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTSegment : NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) NSInteger uniqueId;
@property (nonatomic, assign) SENTSegmentType type;
@property (nonatomic, assign) SENTSegmentCategory category;
@property (nonatomic, assign) SENTSegmentSubcategory subcategory;
@property (nonatomic, strong, nonnull) SENTDate *startDate;
@property (nonatomic, strong, nullable) SENTDate *endDate;
@property (nonatomic, strong, nonnull) NSArray<SENTAttribute *> *attributes;

- (BOOL)isEqualToSegment:(SENTSegment *)segment;

@end
```
