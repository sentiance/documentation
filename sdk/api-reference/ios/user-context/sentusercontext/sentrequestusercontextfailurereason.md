# SENTRequestUserContextFailureReason

{% hint style="info" %}
This type is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
typedef NS_ENUM(NSUInteger, SENTRequestUserContextFailureReason)
```

#### SENTRequestUserContextFailureReasonNoUser

No Sentiance user is present on device. Call createUserWithOptions:completionHandler: to create a user

#### SENTRequestUserContextFailureReasonFeatureNotEnabled

The feature is not enabled for your app.

#### SENTRequestUserContextFailureReasonUserDisabledRemotely

The user is disabled remotely.

