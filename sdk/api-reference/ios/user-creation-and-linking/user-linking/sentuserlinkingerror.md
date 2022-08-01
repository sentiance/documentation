# SENTUserLinkingError

```objectivec
@interface SENTUserLinkingError : NSObject

@property (nonatomic) SENTUserLinkingFailureReason failureReason;
@property (nonatomic, copy) NSString *details;

- (instancetype)init NS_UNAVAILABLE;
- (instancetype)initWithFailureReason:(SENTUserLinkingFailureReason)failureReason
                              details:(NSString *)details NS_DESIGNATED_INITIALIZER;

@end
```
