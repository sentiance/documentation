# SENTDate

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTDate: NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) NSTimeInterval timeIntervalSince1970;
@property (nonatomic, assign, readonly) NSInteger timezoneOffsetInMinutes;
@property (nonatomic, strong, readonly) NSCalendar *calendar;

- (instancetype)initWithNSDate:(NSDate *)date;
- (BOOL)isEqualToDate:(SENTDate *)date;

@end
```
