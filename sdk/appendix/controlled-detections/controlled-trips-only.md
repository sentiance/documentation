---
description: a.k.a Triggered trips
---

# Controlled Trips Only

The default SDK detection mode is set to [automatic detections](automatic-detections.md). This behaviour can be changed by Sentiance to allow recording trips only when you instruct the SDK to do. We call this "controlled trips" or "triggered trips" mode, where automatic SDK detections are disabled.

Once your app has been configured to run in this mode, you can now control when trips are recorded by calling `startTrip` and `stopTrip` as described in [this section](automatic-detections-with-forced-trips.md#starting-a-trip).

## Trip Timeout

In triggered trips mode, the SDK sets timeouts to automatically end trips that have been running for a long period. The duration of this timeout is 2 hours by default, but we can adjust it for your app based on your use case.

To handle trip timeouts, set a listener on the SDK instance:

{% tabs %}
{% tab title="iOS" %}
```objectivec
// Signature
- (void) setTripTimeOutListener: (void (^)(void)) tripDidTimeOut;

// Usage
Sentiance.shared.setTripTimeoutListener {
 // on trip timeout
}
```
{% endtab %}

{% tab title="Android" %}
```kotlin
sentiance.setTripTimeoutListener {   
 // on trip timeout
}
```
{% endtab %}
{% endtabs %}
