# 6. Permissions

To do proper detections, the Sentiance SDK requires a few permissions to be granted by the user at application runtime. The SDK does not ask for these permissions itself. Instead, after explaining to the user why you need each permission, you should present the permission dialogs as part of your application's onboarding flow.

## Location

When running the SDK on Android 6 and above, it is required to ask the user for the location permission. Additionally, if your build targets API level 29 and above, it is also required to ask for the [background location access permission](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS\_BACKGROUND\_LOCATION) (i.e. allow all the time).

{% hint style="warning" %}
On Android 10 and above, without the background location access permission, SDK detections will not work. This permission enables the use of Google Play Service Geofences, which the Sentiance SDK utilizes for detection stability and battery efficiency.
{% endhint %}

The SDK automatically adds the `ACCESS_FINE_LOCATION` and `ACCESS_COARSE_LOCATION` permissions to your app's manifest, however it **does not** add the `ACCESS_BACKGROUND_LOCATION` permission. Instead, you must explicitly add it to your app as follows:

{% code title="AndroidManifest.xml" %}
```markup
<manifest...>
    <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION">
    ...
```
{% endcode %}

## Activity Recognition (Android 10+)

When targeting API level 29 and above, it is required to ask the user for the [activity recognition permission](https://developer.android.com/reference/android/Manifest.permission#ACTIVITY\_RECOGNITION). This permission grants access to the user's physical activity data (biking, walking, etc).

{% hint style="warning" %}
This permission is not mandatory, but when granted, it can help improve the quality of detections. For example, the Sentiance SDK uses activity data to improve the detection of trip starts.
{% endhint %}

The SDK **does not** add the `android.permission.ACTIVITY_RECOGNITION` permission to your app's manifest. Instead, you must explicitly add it to your app as follows:

{% code title="AndroidManifest.xml" %}
```markup
<manifest...>
    <uses-permission android:name="android.permission.ACTIVITY_RECOGNITION">
    ...
```
{% endcode %}

{% hint style="info" %}

{% endhint %}

