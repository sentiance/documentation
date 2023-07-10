# SENTDate

```objectivec
@interface SENTDate: NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) NSTimeInterval timeIntervalSince1970;
@property (nonatomic, assign, readonly) NSInteger timezoneOffsetInMinutes;
@property (nonatomic, strong, readonly) NSCalendar *calendar;

- (instancetype)initWithNSDate:(NSDate *)date;
- (BOOL)isEqualToDate:(SENTDate *)date;

@end
```
