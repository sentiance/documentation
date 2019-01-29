---
description: Ask for location permission (android 6+)
---

# 6. Location Permission

When running the SDK on Android 6 and higher, it's required to ask the user for location permission. The Sentiance SDK does not ask the user for this permission.

In your application flow, after explaining to the user why you need the location permission, you should present a permission check.

An example of this permission check is available [in this PermissionCheckActivity.java](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/PermissionCheckActivity.java) class.

