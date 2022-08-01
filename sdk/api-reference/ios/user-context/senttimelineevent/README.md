# SENTTimelineEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
@interface SENTTimelineEvent : NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) SENTTimelineEventType type;
@property (nonatomic, strong, nonnull) SENTDate *startDate;
@property (nonatomic, strong, nullable) SENTDate *endDate;
@property (nonatomic, assign, readonly) NSInteger durationInSeconds;
@property (nonatomic, assign, readonly) BOOL hasEnded;

- (BOOL)isEqualToTimelineEvent:(SENTTimelineEvent *)timelineEvent;

@end
```
