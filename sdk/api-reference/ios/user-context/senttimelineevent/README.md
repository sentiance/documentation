# SENTTimelineEvent

```objectivec
/// Represents an occurrence of an event that was detected for a user.
@interface SENTTimelineEvent : NSObject <NSSecureCoding, NSCopying>

/// The unique identifier of the event.
@property (nonatomic, strong, nonnull) NSString *eventId;

/**
 The event type. Based on this type, you can cast an event to the
 corresponding event class (e.g. SENTTransportEvent, SENTStationaryEvent)
 to access type specific properties.
 */
@property (nonatomic, assign) SENTTimelineEventType type;

/// The start date of the event.
@property (nonatomic, strong, nonnull) SENTDate *startDate;

/// The end date of the event, if the event has ended. Otherwise, nil.
@property (nonatomic, strong, nullable) SENTDate *endDate;

/// The duration of the event, in seconds. When unknown, this will be equal to SENTDurationUnknown.
@property (nonatomic, assign, readonly) NSInteger durationInSeconds;

@property (nonatomic, assign, readonly) BOOL hasEnded;

- (BOOL)isEqualToTimelineEvent:(SENTTimelineEvent *)timelineEvent;

@end
```
