# 4. Enabling Detections

After creating a Sentiance user, you can enable SDK detections. This will allow the Sentiance SDK to run in the background, and intelligently detect a user's real-world movements, while collecting sensor, location, and motion activity data.

```kotlin
sentiance.enableDetections().addOnCompleteListener { operation ->
    if (operation.isSuccessful) {
        Log.d(TAG, "Successfully enabled detections");
    } else {
        val error = operation.error;
        Log.e(TAG, "Failed to enabled detections due to reason {${error.reason}")
    }
}
```

After detections are successfully enabled, you can determine whether the SDK is able to detect, by checking the detection status:

```kotlin
val detectionStatus = operation.result.detectionStatus // or Sentiance.getInstance(context).detectionStatus
when (detectionStatus) {
    DetectionStatus.ENABLED_AND_DETECTING -> 
        // Detections are enabled and running
    DetectionStatus.ENABLED_BUT_BLOCKED ->
        // Detections are enabled but blocked
    else ->
        // Other enum values don't apply for success scenarios
}
```

If detections are blocked, you can check the SDK status to see what's blocking them. Usually, this is caused by insufficient permissions or a disabled location tracking.

{% hint style="info" %}
#### Enabling Detections Is Persistent

When you enable detections, the SDK will remember this and automatically enable them the next time the app restart. Therefore, you do not need to enable them every time. You only need to make sure that you are [properly initializing the SDK](../../appendix/sdk-initialization.md) during every app startup.
{% endhint %}
