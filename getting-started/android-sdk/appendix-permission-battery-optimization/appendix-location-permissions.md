---
description: Ask for location permission (android 6+)
---

# Location permissions

When running the SDK on Android 6 \(and higher\), it's required to ask the user for location permission. In your application flow, after explaining the user why you need the location permission, you should present a permission check.

An example of this permission check is available [in this PermissionCheckActivity.java class.](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/PermissionCheckActivity.java)

