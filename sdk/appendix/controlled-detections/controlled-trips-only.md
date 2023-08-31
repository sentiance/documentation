---
description: a.k.a Triggered trips
---

# Controlled Trips Only

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

The default SDK detection mode is set to [automatic detections](automatic-detections.md). You can change this behavior and have the SDK record trips only when instructed to do so.

{% tabs %}
{% tab title="iOS" %}
First, enable triggered trips on `SENTConfig`:

```objectivec
[config setIsTriggeredTrip: TRUE];
```
{% endtab %}

{% tab title="Android" %}
First, enable triggered trips on [`SdkConfig`](../../api-reference/android/sdkconfig/):

```java
SdkConfig config = new SdkConfig.Builder(APP_ID, SECRET, notification)
                                .setTriggeredTripsEnabled(true)
                                .build();
```
{% endtab %}
{% endtabs %}

Having done so, you've disabled automatic detection on the SDK. You can now control when trips are recorded by calling `startTrip` and `stopTrip` as described in [this section](automatic-detections-with-forced-trips.md#starting-a-trip).

## Trip Timeout

In triggered trips mode, the SDK sets timeouts to automatically end trips that have been running for a long period. The duration of this timeout is 2 hours by default, but we can adjust it for your app based on your use case.

To handle trip timeouts, set a listener on the SDK instance:

{% tabs %}
{% tab title="iOS" %}
```objectivec
// Signature
- (void) setTripTimeOutListener: (void (^)(void)) tripDidTimeOut;
// Usage
[[SENTSDK sharedInstance] setTripTimeOutListener:tripTimeoutListener];
```
{% endtab %}

{% tab title="Android" %}
```java
sentianceSdk.setTripTimeoutListener(new TripTimeoutListener() {
    @Override
    public void onTripTimeout () {
    }
});
```
{% endtab %}
{% endtabs %}



