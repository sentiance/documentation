# 4. Starting Detections

By starting detections, the Sentiance SDK will intelligently detect a user's trips and stationary moments while collecting sensor, location, and motion activity data.

Starting detections is only allowed after a successful initialization. Ideally, this step is done immediately after initialization succeeds, as this will guarantee that the SDK is detecting as often as possible.

Call the [`start()`](../../api-reference/android/sentiance.md#start) method from the body of [`OnInitCallback.onInitSuccess()`](../../api-reference/android/oninitcallback/#oninitsuccess):

```java
@Override
public void onInitSuccess() {
    Sentiance.getInstance(context).start(new OnStartFinishedHandler() {
        @Override
        public void onStartFinished (SdkStatus sdkStatus) {
        }
    });
}
```

You can pass an [`OnStartFinishedHandler`](../../api-reference/android/onstartfinishedhandler.md) to the [`start()`](../../api-reference/android/sentiance.md#start) method to be notified of the start status. The next section explains about this status and handling general status updates.

{% hint style="info" %}
If you want to have more control over when the Sentiance SDK is doing detections, see [controlled detections](../../appendix/controlled-detections/).
{% endhint %}
