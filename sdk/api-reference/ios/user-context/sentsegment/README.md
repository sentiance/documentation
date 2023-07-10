# SENTSegment

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
