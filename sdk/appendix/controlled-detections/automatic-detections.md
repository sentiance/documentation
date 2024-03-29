# Automatic Detections

Automatic detection mode is the default mode the SDK runs in. In this mode, the SDK automatically determines when a user is in a trip and when he or she is stationary.

Detections start when you `enable` them and all detection requirements are met (on [iOS](../../api-reference/ios/sentsdkstatus.md#candetect) and [Android](../../api-reference/android/sdkstatus/#candetect)).

To stop detections, call the platform specific disableDetections method. This will put the SDK in a stopped state where only regular SDK maintenance tasks will run.

