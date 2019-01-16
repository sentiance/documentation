# Android SDK

## 2019-01-09

### Android SDK \[4.3.0\]

* Ability to disable battery optimization for improved detections \(see [here](https://developers.sentiance.com/docs/sdk/android/integration#battery_optimization)\).
* Updated min required Google Play Location Services version to 12.0.1 \(see [here](https://developers.sentiance.com/docs/sdk/android/integration#google_play_version)\).
* Added new SdkStatus fields \(see [here](https://developers.sentiance.com/docs/sdk/android/status)\).
  * `isBatteryOptimizationEnabled`
  * `isBatterySavingEnabled`
  * `isBackgroundProcessingRestricted`
* Improved detections.
* Minor bug fixes.

## 2018-12-18

### Android SDK \[4.2.9\]

* Updated target API to 28.
* Added `android.permission.FOREGROUND_SERVICE` permission required for Android 9.
* Bug fixes.

## 2018-11-21

### Android SDK \[4.2.8\]

* Improved detection algorithm.

## 2018-11-15

### Android SDK \[4.2.7\]

* Bug fixes.

## 2018-11-12

### Android SDK \[4.2.6\]

* Improved detection algorithm.
* Support for sending mocked locations.
* Minor bug fixes.

## 2018-10-22

### Android SDK \[4.2.5\]

* Improve stationary detection.
* Provide the ability to set the SDK's notification ID.
* Fix google play console warning related to AWS credentials.

## 2018-10-08

### Android SDK \[4.2.4\]

* Disable SDK notifications for triggered trips flavor when no trip is ongoing.
* Prevent LocationService from crashing during startup.

## 2018-10-02

### Android SDK \[4.2.3\]

* Stationary detection improvement.

## 2018-09-24

### Android SDK \[4.2.1\]

* Removed explicit allowBackup param from manifest.
* More SDK logging.
* Wakelock prevention and other minor fixes.

## 2018-08-27

### Android SDK \[4.2.0\]

* Support for meta users.
* Remotely configurable required location providers.

## 2018-08-23

### Android SDK \[4.1.22\]

* Prevent automatic detections in triggered trips mode.

## 2018-08-21

### Android SDK \[4.1.21\]

* Location parameter of CrashCallback.onCrash\(\) is now nullable.
* Vehicle crash detection algorithm update.
* Various bug fixes.

