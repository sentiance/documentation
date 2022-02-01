# 6. Permissions

To do proper detections, the Sentiance SDK requires a few permissions to be granted by the user at application runtime. The SDK does not ask for these permissions itself. Instead, after explaining to the user why you need each permission, you must present the permission dialogs as part of your application's flow.

An example implementation of a permission dialog is available in our [Github app](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/PermissionCheckActivity.java).

## Location

When running the SDK on Android 6 and above, it is required to ask the user for the location permission. Additionally, if your build targets API level 29 and above, it is also required to ask for the [background location access permission](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_BACKGROUND_LOCATION).

{% hint style="warning" %}
On Android 10 and above, without the background location access permission, SDK detections will not work. This permission enables the use of Geofences via Google Play Services, which the Sentiance SDK utilizes for detection stability and battery efficiency.
{% endhint %}

The SDK automatically adds the `ACCESS_FINE_LOCATION` permission to your app's manifest, however it **does not** add the `ACCESS_BACKGROUND_LOCATION` permission \(see [here](../../appendix/android/android-10-update-behavior.md)\). Instead, you must explicitly add it to your app as follows:

{% code title="AndroidManifest.xml" %}
```markup
<manifest...>
    <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION">
    ...
```
{% endcode %}

If any of these permissions is not granted, [`SdkStatus.isLocationPermGranted`](../../api-reference/android/sdkstatus/#islocationpermgranted) will be `false`.

## Activity Recognition \(Android 10+\)

When targeting API level 29 and above, it is required to ask the user for the [activity recognition permission](https://developer.android.com/reference/android/Manifest.permission#ACTIVITY_RECOGNITION). This permission grants access to the user's physical activity data \(idle, walking, etc.\).

{% hint style="warning" %}
The Sentiance platform requires motion activities to improve the SDK detection quality and to do Lifestyle Profiling. Moreover, without this permission, some detections won't be possible \(e.g. running detection\). For any questions, please contact our [support](mailto:support@sentiance.com).
{% endhint %}

The SDK **does not** add the `android.permission.ACTIVITY_RECOGNITION` permission to your app's manifest \(see [here](../../appendix/android/android-10-update-behavior.md)\). Instead, you must explicitly add it to your app as follows:

{% code title="AndroidManifest.xml" %}
```markup
<manifest...>
    <uses-permission android:name="android.permission.ACTIVITY_RECOGNITION">
    ...
```
{% endcode %}

When this permission is not granted, the [`SdkStatus.isActivityRecognitionPermGranted`](../../api-reference/android/sdkstatus/#isactivityrecognitionpermgranted) will be `false`.





