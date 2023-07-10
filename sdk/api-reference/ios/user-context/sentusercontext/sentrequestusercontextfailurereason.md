# SENTRequestUserContextFailureReason

```
typedef NS_ENUM(NSUInteger, SENTRequestUserContextFailureReason)
```

#### SENTRequestUserContextFailureReasonNoUser

No Sentiance user is present on device. Call createUserWithOptions:completionHandler: to create a user

#### SENTRequestUserContextFailureReasonFeatureNotEnabled

The feature is not enabled for your app.

#### SENTRequestUserContextFailureReasonUserDisabledRemotely

The user is disabled remotely.

