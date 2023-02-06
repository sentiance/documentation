# Supported API Levels

| SDK Version     | Minimum API Level (Compilation) | Required API Level for Detections  |
| --------------- | :-----------------------------: | :--------------------------------: |
| 4.0.0 - 4.14.0  |                14               |                 14+                |
| 4.16.0 - 4.22.x |                14               |                 21+                |
| 6.x             |                23               |                 23+                |

If your app supports an API level that is lower than the minimum specified above, check out [this troubleshooting guide](../../troubleshooting/android.md#manifest-merger-failed-uses-sdk-minsdkversion-x-cannot-be-smaller-than-version-y-declared-in-library) to learn how to work around the limitation.

When the SDK is initialized on an Android version that is lower than the one specified in **Required API Level for Detections**, initialization will fail with reason `UNSUPPORTED_OS_VERSION`.

