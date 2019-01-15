# 4. SDK status update handler \(Optional\)

This is optional, but recommended if you want to be kept up-to-date of changes to the SDK status.

```java
OnSdkStatusUpdateHandler statusHandler = new OnSdkStatusUpdateHandler() {
    @Override
    public void onSdkStatusUpdate(SdkStatus status) {
    }
};
```

Then set it on the `SdkConfig.Builder`:

```java
SdkConfig sdkConfig = new SdkConfig.Builder(APP_ID, SECRET, notification)
        .setOnSdkStatusUpdateHandler(statusHandler)
        .build();
```

A sample `OnSdkStatusUpdateHandler` implementation can be found on [Github](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/SdkStatusUpdateHandler.java). For more information related to the `SdkStatus` class, see [this guide](https://developers.sentiance.com/docs/sdk/android/status).

