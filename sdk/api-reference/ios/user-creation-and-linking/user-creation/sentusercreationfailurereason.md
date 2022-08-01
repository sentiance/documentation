# SENTUserCreationFailureReason

```objectivec
typedef NS_ENUM(NSUInteger, SENTUserCreationFailureReason)
```

| Type                                                    | Description                                                                                  |
| ------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **SENTUserCreationFailureReasonSdkResetInProgress**     | A user cannot be created while the SDK is being reset.                                       |
| **SENTUserCreationFailureReasonUserCreationInProgress** | User creation is already in progress.                                                        |
| **SENTUserCreationFailureReasonUserAlreadyExists**      | A user already exists. There cannot be more than one Sentiance user at a time on the device. |
| **SENTUserCreationFailureReasonNetworkError**           | A network error occurred.                                                                    |
| **SENTUserCreationFailureReasonServerError**            | A server error occurred.                                                                     |
| **SENTUserCreationFailureReasonUnexpectedError**        | An unexpected error occurred.                                                                |
| **SENTUserCreationFailureReasonAppSideLinkingFailed**   | The application failed to complete the user linking step.                                    |
