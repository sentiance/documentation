# SdkStatus

This class exposes the status of the Sentiance SDK. You can get an instance of this object in two ways.

* Using [`OnSdkStatusUpdateHandler`](../onsdkstatusupdatehandler.md) as explained in the [SDK Status Updates](../../../getting-started/android-sdk/sdk-status-updates.md) step of the quick start guide;
* using the [`getSdkStatus()`](../sentiance.md#getsdkstatus) method.

A sample [`OnSdkStatusUpdateHandler`](../onsdkstatusupdatehandler.md) implementation can be found on our [Github](https://github.com/sentiance/sdk-starter-android/blob/master/app/src/main/java/com/sentiance/sdkstarter/SdkStatusUpdateHandler.java). 

|  |  |
| :--- | :--- |
| [StartStatus](startstatus.md)  | [startStatus](startstatus.md) |
| boolean  | [canDetect](./#candetect) |
| boolean  | [isRemoteEnabled](./#isremoteenabled) |
| boolean  | [isLocationPermGranted](./#islocationpermgranted) |
| boolean | [isActivityRecognitionPermGranted](./#isactivityrecognitionpermgranted) |
| [LocationSetting](locationsetting.md)  | [locationSetting](./#locationsetting) |
| boolean  | [isAirplaneModeEnabled](./#isairplanemodeenabled) |
| boolean  | [isLocationAvailable](./#islocationavailable) |
| boolean  | [isAccelPresent](./#isaccelpresent) |
| boolean  | [isGyroPresent](./#isgyropresent) |
| boolean  | [isGpsPresent](./#isgpspresent) |
| boolean  | [isGooglePlayServicesMissing](./#isgoogleplayservicesmissing) |
| boolean | [isBatteryOptimizationEnabled](./#isbatteryoptimizationenabled) |
| boolean | [isBatterySavingEnabled](./#isbatterysavingenabled) |
| boolean | [isBackgroundProcessingRestricted](./#isbackgroundprocessingrestricted) |
| [QuotaStatus](quota-status.md)  | [wifiQuotaStatus](./#wifiquotastatus) |
| [QuotaStatus](quota-status.md)  | [mobileQuotaStatus](./#mobilequotastatus) |
| [QuotaStatus](quota-status.md)  | [diskQuotaStatus](./#diskquotastatus) |



### `startStatus`

> A [`StartStatus`](startstatus.md) enum representing the start state of the SDK detections..

### `canDetect`

> A synthesis of many of the other fields \([`isRemoteEnabled`](./#isremoteenabled), [`isLocationPermGranted`](./#islocationpermgranted), [`locationSetting`](./#locationsetting), [`isGpsPresent`](./#isgpspresent), [`isGooglePlayServicesMissing`](./#isgoogleplayservicesmissing), [`isAirplaneModeEnabled`](./#isairplanemodeenabled), [`isLocationAvailable`](./#islocationavailable), [`diskQuotaStatus`](./#diskquotastatus), and [`isBackgroundProcessingRestricted`](./#isbackgroundprocessingrestricted)\).
>
> This field indicates whether the conditions are suitable for the SDK to run its detections. If this is true, it does not mean that detections are running; that also depends on [`startStatus`](./#startstatus).

### `isRemoteEnabled`

> Whether the user is enabled by the Sentiance API. This field can be used in combination with the rollout settings on the Audience Manager.

### `isLocationPermGranted`

> Whether the user has granted location permission to the app.

### `isActivityRecognitionPermGranted`

> Whether the activity recognition permission has been granted.

### `locationSetting`

> A [`LocationSetting`](locationsetting.md) enum representing the location mode setting on the device.

### `isAirplaneModeEnabled`

> Whether the device is in airplane mode.

### `isLocationAvailable`

> Whether the device's location is available. Several reasons may lead to failure to obtain a location \(e.g. no GPS or network signal\).

### `isAccelPresent`

> Whether an accelerometer sensor is present on the device.

### `isGyroPresent`

> Whether a gyroscope sensor is present on the device.

### `isGpsPresent`

> Whether a GPS sensor is present on the device.

### `isGooglePlayServicesMissing`

> Whether Google Play Services is missing from the device.

### `isBatteryOptimizationEnabled`

> Whether [battery optimization](../../../appendix/android/android-battery-optimization.md) is enabled for the application. This will be set to `false` for devices running Lollipop and lower.

### `isBatterySavingEnabled`

> Whether battery saving is enabled on the device. This will be set to `false` for devices running Kitkat and lower.

### `isBackgroundProcessingRestricted`

> Whether background processing is [restricted](https://developer.android.com/reference/android/app/ActivityManager#isBackgroundRestricted%28%29) for the application. When `true`, SDK detections will be will be paused. This will be set to `false` for devices running Oreo and lower.

### `wifiQuotaStatus`

> A [`QuotaStatus`](quota-status.md) enum representing the WiFi quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the [`getWiFiQuotaUsage()`](../sentiance.md#getwifiquotausage), [`getWiFiQuotaLimit()`](../sentiance.md#getwifiquotalimit).

### `mobileQuotaStatus`

> A [`QuotaStatus`](quota-status.md) enum representing the mobile data quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the [`getMobileQuotaUsage()`](../sentiance.md#getmobilequotausage), [`getMobileQuotaLimit()`](../sentiance.md#getmobilequotalimit).

### `diskQuotaStatus`

> A [`QuotaStatus`](quota-status.md) enum representing the disk quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the [`getDiskQuotaUsage()`](../sentiance.md#getdiskquotausage), [`getDiskQuotaLimit()`](../sentiance.md#getdiskquotalimit).

