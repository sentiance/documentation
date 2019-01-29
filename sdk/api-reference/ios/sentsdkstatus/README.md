# SENTSdkStatus

The status of the Sentiance SDK is exposed in the `SENTSdkStatus` object. You can get an instance of this object in two ways.

* using `setDidReceiveSdkStatusUpdate` as explained in the configuration step of quick start guide.
* using the `getSdkStatus` method.

|  |  |
| :--- | :--- |
| [SENTStartStatus](sentstartstatus.md)  | [startStatus](./#startstatus) |
| boolean  | [canDetect](./#candetect) |
| boolean  | [isRemoteEnabled](./#isremoteenabled) |
| boolean  | [isLocationPermGranted](./#islocationpermgranted) |
| boolean  | [isBgAccessPermGranted](./#isbgaccesspermgranted) |
| boolean  | [isAirplaneModeEnabled](./#isairplanemodeenabled) |
| boolean  | [isAccelPresent](./#isaccelpresent) |
| boolean  | [isGyroPresent](./#isgyropresent) |
| boolean  | [isGpsPresent](./#isgpspresent) |
| [SENTQuotaStatus](sentquotastatus.md)  | [wifiQuotaStatus](./#wifiquotastatus) |
| [SENTQuotaStatus](sentquotastatus.md)  | [mobileQuotaStatus](./#mobilequotastatus) |
| [SENTQuotaStatus](sentquotastatus.md)  | [diskQuotaStatus](./#diskquotastatus) |

### `startStatus`

> A [`SENTStartStatus`](sentstartstatus.md) enum representing the start state of the SDK detections..

### `canDetect`

> A synthesis of many of the other fields \([`isRemoteEnabled`](./#isremoteenabled), [`isLocationPermGranted`](./#islocationpermgranted),  [`isGpsPresent`](../../android/sdkstatus/#isgpspresent)\).
>
> This field indicates whether the conditions are suitable for the SDK to run its detections. If this is true, it does not mean that detections are running; that also depends on [`startStatus`](./#startstatus).

### `isRemoteEnabled`

> Whether the user is enabled by the Sentiance API. This field can be used in combination with the rollout settings on the Audience Manager.

### `isLocationPermGranted`

> Whether the user has granted location permission to the app.

### `isBgAccessPermGranted`

> Whether background access permission has been granted.

### `isAirplaneModeEnabled`

> Whether the device is in airplane mode.

### `isAccelPresent`

> Whether an accelerometer sensor is present on the device.

### `isGyroPresent`

> Whether a gyroscope sensor is present on the device.

### `isGpsPresent`

> Whether a GPS sensor is present on the device.

### `wifiQuotaStatus`

> A [`SENTQuotaStatus`](sentquotastatus.md) enum representing the WiFi quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the `getWiFiQuotaUsage`, `getWiFiQuotaLimit`.

### `mobileQuotaStatus`

> A [`SENTQuotaStatus`](sentquotastatus.md) enum representing the mobile data quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the `getMobileQuotaUsage`, `getMobileQuotaLimit`.

### `diskQuotaStatus`

> A [`SENTQuotaStatus`](sentquotastatus.md) enum representing the disk quota status of the SDK.
>
> The actual usages and limits in bytes can be obtained using the `getDiskQuotaUsage`, `getDiskQuotaLimit`.

