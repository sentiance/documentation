---
description: Error type returned in case of User Context Request Failed.
---

# SENTRequestUserContextError

{% hint style="info" %}
This type is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

### failureReason

```
@property (nonatomic) SENTRequestUserContextFailureReason failureReason;
```



### initWithFailureReason:

```
- (instancetype)initWithFailureReason:(SENTRequestUserContextFailureReason)failureReason
```
