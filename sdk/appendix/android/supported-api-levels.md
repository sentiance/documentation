# Supported API Levels

<table><thead><tr><th width="172.33333333333331">SDK Version</th><th align="center">Minimum API Level (Compilation)</th><th align="center">Required API Level for Detections </th></tr></thead><tbody><tr><td>4.0.0 - 4.14.0</td><td align="center">14</td><td align="center">14+</td></tr><tr><td>4.16.0 - 4.22.x</td><td align="center">14</td><td align="center">21+</td></tr><tr><td>6.x</td><td align="center">23</td><td align="center">23+</td></tr></tbody></table>

If your app supports an API level that is lower than the minimum specified above, you can check out [this troubleshooting guide](../../troubleshooting/android.md#manifest-merger-failed-uses-sdk-minsdkversion-x-cannot-be-smaller-than-version-y-declared-in-library) to learn how to work around the limitation.

When the SDK is initialized on an Android version that has a lower API level than the one specified in **Required API Level for Detections**, initialization will fail with reason `UNSUPPORTED_OS_VERSION`.

