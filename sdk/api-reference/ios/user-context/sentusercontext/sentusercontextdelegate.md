# SENTUserContextDelegate

{% hint style="info" %}
This protocol is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

{% tabs %}
{% tab title="Swift" %}
```swift
public protocol SENTUserContextDelegate : NSObjectProtocol {
    optional func didUpdate(_ userContext: SENTUserContext, 
             forCriteriaMask criteriaMask: SENTUserContextUpdateCriteria)
}
```
{% endtab %}

{% tab title="Objective-C" %}
```objectivec
@protocol SENTUserContextDelegate <NSObject>
@optional
- (void)didUpdateUserContext:(SENTUserContext *)userContext
             forCriteriaMask:(SENTUserContextUpdateCriteria)criteriaMask;
@end
```
{% endtab %}
{% endtabs %}

