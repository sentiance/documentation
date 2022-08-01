# SdkStatus

This class exposes the status of the Sentiance SDK. You can get an instance of this object in two ways.

* Using [`SdkStatusUpdateListener`](../sdkstatusupdatelistener.md) as explained in the [SDK Status Updates](../../../getting-started/android-sdk/sdk-status-updates.md) step of the quick start guide;
* using the [`getSdkStatus()`](../sentiance.md.md#getsdkstatus) method.

A sample [`OnSdkStatusUpdateHandler`](../onsdkstatusupdatehandler.md) implementation can be found on our [Github](https://github.com/sentiance/sample-apps-android/blob/main/app/src/main/java/com/example/sentiancesdksample\_app\_android/SdkStatusUpdateHandler.kt).&#x20;

## SdkStatus API

### `detectionStatus`

> A [`detectionStatus`](../detectionstatus.md) enum representing the detection status of the SDK.

### `startStatus` _(deprecated)_

{% hint style="warning" %}
**Deprecated**

Use `detectionStatus` instead.
{% endhint %}

> A [`StartStatus`](startstatus.md) enum representing the start state of the SDK detections.

### `canDetect`

> A synthesis of the following fields, indicating whether the conditions are suitable for the SDK to run its detections:
>
> * isRemoteEnabled
> * locationPermission
> * locationSetting
> * isGpsPresent
> * isGooglePlayServicesMissing
> * isAirplaneModeEnabled
> * isPreciseLocationPermGranted
> * isLocationAvailable
> * diskQuotaStatus
> * isBackgroundProcessingRestricted

### `isRemoteEnabled`

> Whether the user is enabled on the Sentiance Platform. By default, all users are enabled on the Sentiance Platform. A user may get disabled during creation if, for example, the device is a tablet and the same user already exists on a phone. Sentiance can also disable users selectively under certain conditions (e.g. due to a misbehaving SDK).
>
> An enabled user is required to do detections.

### `isPreciseLocationPermGranted`

> Whether the user has granted precise location permission to the app. See [approximate location](https://developer.android.com/about/versions/12/approximate-location).
>
> Precise location permission is required to do detections.

### `isActivityRecognitionPermGranted`

> Whether the activity recognition permission has been granted.

### `locationSetting`

> A [`LocationSetting`](locationsetting.md) enum representing the location setting currently set in the device settings.
>
> A location setting of `OK` or `BATTERY_SAVING` are required to do detections.

### `isAirplaneModeEnabled`

> Whether the device is in airplane mode.
>
> Airplane mode must be disabled to do detections.

### `isLocationAvailable`

> Whether location information is available.
>
> Generally, when the device location setting is in an acceptable state, and all required location related permissions are granted, this property will be `true`. However, under certain conditions, location data may still be unavailable, in which case this property will be `false`. Once location data becomes available again, the SDK will automatically update this property and resume detections if possible.

### `isAccelPresent`

> Whether the device has an accelerometer.

### `isGyroPresent`

> Whether the device has a gyroscope.

### `isGpsPresent`

> Whether the device has a GPS.
>
> A GPS is required to do detections.

### `isGooglePlayServicesMissing`

> Whether Google Play Services is missing.
>
> Google Play Services is required to do detections.

### `isBatteryOptimizationEnabled`

> Whether [battery optimization](../../../appendix/android/android-battery-optimization.md) is enabled for the application.
>
> On some devices, battery optimization can have a negative impact on apps running in the background. This is due to OEM specific customizations of Android's battery optimization feature. As such, disabling battery optimization is generally recommended for quality detections, if possible.

### `isBatterySavingEnabled`

> Whether battery saving is enabled on the device.
>
> When battery saving is enabled, it can have a negative impact on apps running in the background. As a result, SDK detection quality may be impacted.

### `isBackgroundProcessingRestricted`

> Whether background processing is [restricted](https://developer.android.com/reference/android/app/ActivityManager#isBackgroundRestricted\(\)) for the application. This will be set to `false` for devices running Oreo and lower.
>
> Unrestricted background processing is required to do detections.

### `isSchedulingExactAlarmsPermitted`

> Whether scheduling exact alarms is permitted. This is normally permitted, unless the user has manually revoked the permission from the device settings. When the permission is not granted, it can have a negative impact on the detection quality.

### `locationPermission`

> A [`LocationPermission`](../sdkconfig/locationpermission.md) enum representing the location accessibility permission.
>
> Under most circumstances, an `ALWAYS` permission is required to do detections.

### `wifiQuotaStatus`

> A [`QuotaStatus`](quota-status.md) enum representing the WiFi quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the [`getWiFiQuotaUsage()`](../sentiance.md.md#getwifiquotausage), [`getWiFiQuotaLimit()`](../sentiance.md.md#getwifiquotalimit).

### `mobileQuotaStatus`

> A [`QuotaStatus`](quota-status.md) enum representing the mobile data quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the [`getMobileQuotaUsage()`](../sentiance.md.md#getmobilequotausage), [`getMobileQuotaLimit()`](../sentiance.md.md#getmobilequotalimit).

### `diskQuotaStatus`

> A [`QuotaStatus`](quota-status.md) enum representing the disk quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the [`getDiskQuotaUsage()`](../sentiance.md.md#getdiskquotausage), [`getDiskQuotaLimit()`](../sentiance.md.md#getdiskquotalimit).
