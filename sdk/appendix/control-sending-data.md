# Control Sending Data

The Sentiance SDK optimizes in which circumstances data submission occurs, to minimize network and battery usage.

For certain users with specific usage patterns \(e.g. someone who rarely connects to Wi-Fi\), it could take a long time before detections are finally submitted.

If you want to override the default behavior, you can initiate a force submission of detections. Ideally, you use this method only after explaining to the user that your app will consume more bandwidth in case the device is not connected to Wi-Fi.

{% tabs %}
{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] submitDetections:^{
    // If any data was pending, this now is submitted.
} failure:^{
    // Something went wrong with submitting data.
}];
```
{% endtab %}

{% tab title="Android" %}
```java
sentianceSdk.submitDetections(new SubmitDetectionsCallback() {
    @Override
    public void onSuccess() {
    }
    @Override
    public void onFailure() {
    }
});
```
{% endtab %}
{% endtabs %}

In order to know when it makes sense to do this, you can check the disk, mobile network and WiFi quotas of the [`SdkStatus`](../api-reference/android/sdkstatus/) and [`SENTSdkStatus`](../api-reference/ios/sentsdkstatus/) objects.

