# 6. Permissions

To do proper detections, the Sentiance SDK requires a few permissions to be granted by the user at application runtime. The SDK does not ask for these permissions itself. Instead, after explaining to the user why you need each permission, you must present the permission dialogs as part of your application's flow.

An example implementation of a permission dialog is available in our [Github app](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/PermissionCheckActivity.java).

## Location

When running the SDK on Android 6 and above, it is required to ask the user for the location permission. Additionally, if your build targets API level 29 and above, it is also required to ask for the [background location access permission](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_BACKGROUND_LOCATION).

{% hint style="warning" %}
On Android 10 and above, without the background location access permission, SDK detections will not work. This permission enables the use of Geofences via Google Play Services, which the Sentiance SDK utilizes for detection stability and battery efficiency.
{% endhint %}

The SDK automatically adds the `ACCESS_FINE_LOCATION` and `ACCESS_BACKGROUND_LOCATION` permissions to your app's manifest. If any of these permissions is not granted, [`SdkStatus.isLocationPermGranted`](../../api-reference/android/sdkstatus/#islocationpermgranted) will be `false`.

## Activity Recognition \(Android 10+\)

When targeting API level 29 and above, it is required to ask the user for the [activity recognition permission](https://developer.android.com/reference/android/Manifest.permission#ACTIVITY_RECOGNITION). This permission grants access to the user's physical activity data \(idle, walking, etc.\).

{% hint style="warning" %}
If this permission is not granted, the SDK detection quality will be degraded.
{% endhint %}

The SDK **does not** add the `android.permission.ACTIVITY_RECOGNITION` permission to your app's manifest \(for the reason stated below\). Instead, you must explicitly add it to your app as follows:

{% code-tabs %}
{% code-tabs-item title="AndroidManifest.xml" %}
```markup
<uses-permission android:name="android.permission.ACTIVITY_RECOGNITION">
```
{% endcode-tabs-item %}
{% endcode-tabs %}

When this permission is not granted, the [`SdkStatus.isActivityRecognitionPermGranted`](../../api-reference/android/sdkstatus/#isactivityrecognitionpermgranted) will be `false`.

{% hint style="danger" %}
**If you're not targeting API level 29**

The [Android documentation](https://developer.android.com/about/versions/10/privacy/changes#physical-activity-recognition) states that when targeting API level 28 and lower, Android will auto-grant this permission on Android 10 as long as the `com.google.android.gms.permission.ACTIVITY_RECOGNITION` permission is present in the manifest \(already added by the Sentiance SDK\).

However, note that by adding`android.permission.ACTIVITY_RECOGNITION` to your manifest even when targeting API level 28, you will break the auto-grant feature. As a result, do not add this permission to your manifest. Only after updating your target API level to 29, add the permission and ask the user to grant it.
{% endhint %}





