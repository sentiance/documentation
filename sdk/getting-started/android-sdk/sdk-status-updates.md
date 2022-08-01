# 5. SDK Status Updates

You can stay up to date with changes to the SDK's detection status by setting a status update listener. Status updates are usually triggered by changes to the device state and settings (e.g. airplane mode, location permission, etc). Handling these updates gives you the chance to instruct your user, when applicable, to properly adjust the device setting for optimal SDK detections.

```kotlin
Sentiance.getInstance(this).setSdkStatusUpdateListener { status -> 
    // Check status.detectionStatus to determine whether detections are 
    // running, and if not, check the various status fields to see what 
    // might be blocking the detections.
}
```

Check [this](../../api-reference/android/sdkstatus/) reference page to see the various status fields reported by the SDK.
