# 5. SDK Status Updates

This step is optional, but recommended if you want to be kept up-to-date with changes to the SDK detection status. Status updates are usually triggered by changes to the device state and settings \(e.g. airplane mode, location permission/mode, etc.\). Handling these updates gives you the chance to instruct your user, when applicable, to properly adjust the device configuration for optimal SDK detections.

To get notified of status updates, implement the [`OnSdkStatusUpdatehandler`](../../api-reference/android/onsdkstatusupdatehandler.md) interface:

```java
OnSdkStatusUpdateHandler statusHandler = new OnSdkStatusUpdateHandler() {
    @Override
    public void onSdkStatusUpdate(SdkStatus status) {
    }
};
```

Then set it on the [`SdkConfig.Builder`](../../api-reference/android/sdkconfig/sdkconfig-builder.md):

```java
SdkConfig sdkConfig = new SdkConfig.Builder(APP_ID, SECRET, notification)
        .setOnSdkStatusUpdateHandler(statusHandler)
        .build();
```

You will now receive updates as an [`SdkStatus`](../../api-reference/android/sdkstatus/) object. A sample [`OnSdkStatusUpdateHandler`](../../api-reference/android/onsdkstatusupdatehandler.md) implementation can be found on our [Github](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/SdkStatusUpdateHandler.java) page.

