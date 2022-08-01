# SENTUserCreationError

```objectivec
@interface SENTUserCreationError : NSObject
```

###

### failureReason

```objectivec
@property (nonatomic) SENTUserCreationFailureReason failureReason;
```

### details

```objectivec
@property (nonatomic, copy) NSString *details;
```

### initWithFailureReason: details:

```objectivec
- (instancetype)initWithFailureReason:(SENTUserCreationFailureReason)failureReason
                              details:(NSString *)details;
```
