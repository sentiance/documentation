# Android

## 4.5.1 - 2019-02-20

#### Added

* Capture unexpected exceptions and errors during SDK init, and fail with reason [`InitIssue.INITIALIZATION_ERROR`](../api-reference/android/oninitcallback/initissue.md).
* Minor detection improvement.

#### Changed

* [`OnInitCallback.onInitFailure()`](../api-reference/android/oninitcallback/#oninitfailure) now passes a [`Throwable`](https://developer.android.com/reference/java/lang/Throwable) as an additional parameter in case of the aforementioned [`InitIssue.INITIALIZATION_ERROR` ](../api-reference/android/oninitcallback/initissue.md).

#### Fixed

* Stuck stationary issue.
* Alarms not triggering on Samsung.

## 4.5.0 - 2019-02-11

#### Added

* Upload device location-mode, battery-saving state, and battery optimization config to the Sentiance platform.
* Capture hourly heartbeat events to track SDK runtime.
* Support uploading select SDK events \(e.g. heartbeat\) to the Sentiance platform over mobile data.

#### Fixed

* [`TransportMode`](../api-reference/android/trip/transportmode.md) enum obfuscation issue.

## 4.4.0 - 2019-01-17

#### Added

* Support for uploading SDK logs over mobile data.
* Detection improvements to some Samsung and Huawei devices.

#### Changed

* Prevent Sentiance credentials change for an already authenticated user \(init will fail with [`CHANGED_CREDENTIALS`](../api-reference/android/initstate.md)\).
* Prevent premature user access token refreshes.

#### Deprecated

* `Sentiance.isInitialized()` is now deprecated. Use [`Sentiance.getInitState()`](../api-reference/android/sentiance.md#getinitstate) instead, which returns an [`InitState`](../api-reference/android/initstate.md) enum.

#### Fixed

* Minor bug fixes.

## 4.3.0 - 2019-01-09

#### Added

* Ability to disable battery optimization for improved detections \(see [here](../appendix/android/android-battery-optimization.md)\).
* New [`SdkStatus`](../api-reference/android/sdkstatus/) fields.
  * `isBatteryOptimizationEnabled`
  * `isBatterySavingEnabled`
  * `isBackgroundProcessingRestricted`

#### Changed

* Updated min required Google Play Location Services version to 12.0.1.
* Improved detections.

#### Fixed

* Minor bug fixes.

## 4.2.9 - 2018-12-18

#### Added

* `android.permission.FOREGROUND_SERVICE` permission required for Android 9.

#### Changed

* Updated target API to 28.

#### Fixed

* Bug fixes.

## 4.2.8 - 2018-11-21

#### Changed

* Improved detection algorithm.

## 4.2.7 - 2018-11-15

#### Fixed

* Bug fixes.

## 4.2.6 - 2018-11-12

#### Added

* Support for sending mocked locations.

#### Changed

* Improved detection algorithm.

#### Fixed

* Minor bug fixes.

## 4.2.5 - 2018-10-22

#### Added

* Provide the ability to set the SDK's notification ID.

#### Changed

* Improve stationary detection.

#### Fixed

* Fix google play console warning related to AWS credentials.

## 4.2.4 - 2018-10-08

#### Changed

* Disable SDK notifications for triggered trips flavor when no trip is ongoing.

#### Fixed

* Prevent LocationService from crashing during startup.

## 4.2.3 - 2018-10-02

#### Changed

* Stationary detection improvement.

## 4.2.1 - 2018-09-24

#### Added

* More SDK logging.

#### Changed

* Removed explicit allowBackup param from manifest.

#### Fixed

* Wakelock prevention and other minor fixes.

## 4.2.0 - 2018-08-27

#### Added

* Support for meta users.
* Remotely configurable required location providers.

## 4.1.22 - 2018-08-23

#### Fixed

* Prevent automatic detections in triggered trips mode.

## 4.1.21 - 2018-08-21

#### Changed

* Location parameter of `CrashCallback.onCrash()` is now nullable.
* Vehicle crash detection algorithm update.

#### Fixed

* Various bug fixes.

