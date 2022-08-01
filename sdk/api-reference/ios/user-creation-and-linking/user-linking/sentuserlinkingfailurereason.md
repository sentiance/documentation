# SENTUserLinkingFailureReason

```objectivec
typedef NS_ENUM(NSUInteger, SENTUserLinkingFailureReason)
```

| Type                                                 | Description                                                                                       |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **SENTUserLinkingFailureReasonNoUser**               | No user present on the device. Call createUserWithOptions: completionHandler: to create a user.   |
| **SENTUserLinkingFailureReasonUserAlreadyLinked**    | The user is already linked.                                                                       |
| **SENTUserLinkingFailureReasonNetworkError**         | A network error occurred.                                                                         |
| **SENTUserLinkingFailureReasonServerError**          | A server error occurred.                                                                          |
| **SENTUserLinkingFailureReasonUserDisabledRemotely** | The user is disabled remotely.                                                                    |
| **SENTUserLinkingFailureReasonUnexpectedError**      | An unexpected error occurred. Check the corresponding SENTUserLinkingError.details for more info. |
| **SENTUserLinkingFailureReasonAppSideLinkingFailed** | The application failed to complete the user linking step.                                         |
