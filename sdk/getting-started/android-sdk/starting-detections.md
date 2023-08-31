# 4. Starting Detections

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

By starting detections, the Sentiance SDK will intelligently detect a user's real-world movements while collecting sensor, location, and motion activity data.

Starting detections is only allowed after a successful initialization. Ideally, this step is done immediately after initialization succeeds, as this will guarantee that the SDK is detecting as early and often as possible.

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

{% hint style="warning" %}
The SDK holds a [weak reference](https://docs.oracle.com/javase/7/docs/api/java/lang/ref/WeakReference.html) to the handler to avoid leaking your Activity or app component. Declare the handler at the class level if you want to make sure the callback gets invoked after `onInitSuccess` returns.
{% endhint %}

{% hint style="info" %}
If you want to have more control over when the Sentiance SDK is doing detections, see [controlled detections](../../appendix/controlled-detections/).
{% endhint %}

