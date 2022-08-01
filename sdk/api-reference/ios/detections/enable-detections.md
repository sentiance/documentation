# Enable Detections

### SENTEnableDetectionsResult

```objectivec
@interface SENTEnableDetectionsResult : SENTDetectionsOperationResult
```



### SENTEnableDetectionsError

```objectivec
@interface SENTEnableDetectionsError : NSObject
```



### SENTEnableDetectionsFailureReason

```objectivec
typedef NS_ENUM(NSUInteger, SENTEnableDetectionsFailureReason)
```

| Type                                                      | Description                                                                                   |
| --------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **SENTEnableDetectionsFailureReasonNoUse**r               | No user present on the device. Call createUserWithOptions:completionHandler:to create a user. |
| **SENTEnableDetectionsFailureReasonPastExpiryDate**       | Expiry date is in past.                                                                       |
| **SENTEnableDetectionsFailureReasonUserDisabledRemotely** | The user is disabled remotely.                                                                |

###

### SENTEnableDetectionsCompletionHandler

```objectivec
typedef void (^SENTEnableDetectionsCompletionHandler)(SENTEnableDetectionsResult *_Nullable result,
                                                      SENTEnableDetectionsError *_Nullable error);
```
