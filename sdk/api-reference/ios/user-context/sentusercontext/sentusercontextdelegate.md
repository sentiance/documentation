# SENTUserContextDelegate

{% hint style="info" %}
This protocol is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}



```objectivec
@protocol SENTUserContextDelegate <NSObject>
@optional
- (void)didUpdateUserContext:(SENTUserContext *)userContext
             forCriteriaMask:(SENTUserContextUpdateCriteria)criteriaMask;
@endbj
```
