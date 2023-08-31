# Automatic Detections

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Automatic detection mode is the default mode the SDK runs in. In this mode, the SDK automatically determines when a user is in a trip and when he or she is stationary.

Detections start when you call the `start` method and all detection requirements are met \(on [iOS](../../api-reference/ios/sentsdk/sentsdkstatus.md#candetect) and [Android](../../api-reference/android/sdkstatus/#candetect)\).

To stop detections, call the `stop` method. This will put the SDK in a stopped state where only regular SDK maintenance tasks will run.



