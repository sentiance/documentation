# Detecting Vehicle Crashes

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

The Sentiance SDK can be configured to detect vehicle accidents/crashes during trips. You can be notified of these crash events by setting a callback as follows:

{% tabs %}
{% tab title="iOS" %}
```objectivec
// Signature
- (void)setCrashListener:(void (^)(NSDate *date, CLLocation *lastKnownLocation))crashCallback;
// Usage
[[SENTSDK sharedInstance] setCrashListener:^(NSDate *date, CLLocation *lastKnownLocation) {
        // Handle vehicle crash event
    }];
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
