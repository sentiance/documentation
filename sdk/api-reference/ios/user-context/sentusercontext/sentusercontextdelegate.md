# SENTUserContextDelegate

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

