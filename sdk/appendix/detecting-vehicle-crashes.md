# Detecting Vehicle Crashes

The Sentiance SDK can be configured to detect vehicle accidents/crashes during trips. You can be notified of these crash events by setting a callback as follows:

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
sentianceSdk.setCrashCallback(new CrashCallback() {
    @Override
    public void onCrash(long time, @Nullable Location lastKnownLocation) {
        // crash detected
    }
});
```
{% endtab %}
{% endtabs %}

