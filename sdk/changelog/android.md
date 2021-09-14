# Android

## \[4.19.3\] - 14 Sep 2021

#### Fixed <a id="markdown-header-added"></a>

* Occasional SecurityException when accessing the ConnectivityManager on Android 11+ devices.
* Failure to detect some phone calls during trips.
* A rare occurrence of a NullPointerException during internal SDK message handling.

## \[4.19.2\] - 1 Jul 2021

#### Fixed <a id="markdown-header-added"></a>

* Failure to initialize the SDK on some emulator images due to a divide by zero error.

## \[4.19.1\] - 9 Jun 2021

#### Fixed <a id="markdown-header-added"></a>

* Failure to run crash detection immediately after resetting the SDK.

## \[4.19.0\] - 14 Apr 2021

#### Added <a id="markdown-header-added"></a>

* Support for tracking app foreground and background state changes.
* Support for collecting accelerometer range and max supported frequency.
* Improve detection of tablet devices by taking the device's smallest screen width into account.

**Changed**

* Use existing authentication token when submitting a token refresh request.
* Add fail-fast mechanism during third party user linking if linking has not been completed.

#### Fixed <a id="markdown-header-fixed"></a>

* Improve handling of out of order sensor data
* Fix skipped events in some rare cases.

## \[4.18.1\] - 8 Feb 2021

#### Fixed

* Stability improvements to the user authentication and sensor data collection.

## \[4.18.0\] - 14 Jan 2021

#### Added

* An improved and a more accurate vehicle crash detection, backed by a machine learning model. You must switch to using the new Sentiance API method [`setVehicleCrashListener(VehicleCrashListener)`](../api-reference/android/sentiance.md#setvehiclecrashlistener) to activate it.
* A new method to help test your crash detection integration. See [`invokeDummyCrash()`](../api-reference/android/sentiance.md#invokedummycrash).
* A new method to check if crash detection is supported on the device for a specific trip type. See [`isCrashDetectionSupported(TripType)`](../api-reference/android/sentiance.md#iscrashdetectionsupported).

#### Changed

* Points of interest data is no longer provided in the [`StationaryInfo`](../api-reference/android/stationaryinfo.md) object \(returned by [`getStationaryInfo()`](../api-reference/android/useractivity.md#getstationaryinfo)\) by default. If you use this data, please reach out to us before updating to this SDK version.
* On Android 9 and above, when [background execution is restricted](https://developer.android.com/reference/android/app/ActivityManager#isBackgroundRestricted%28%29) for your app \(by the user or an OS power saving feature\), SDK detections will no longer run. An [`SdkStatus`](../api-reference/android/sdkstatus/) update will be delivered to your app, with `startStatus` set to `PENDING` and `isBackgroundProcessingRestricted` set to `true` so that you can take the appropriate action.
* Library dependency changes:
  * Removed compile-time dependency on `com.google.code.findbugs:jsr305`
  * Added runtime dependency on `org.tensorflow:tensorflow-lite:2.2.0`. This dependency adds native libraries to your app. To limit their architectures, see [here](../troubleshooting/android.md#exclude-native-libraries-for-unsupported-architectures).

#### Deprecated

*  [`setCrashCallback(CrashCallback)`](../api-reference/android/sentiance.md#setcrashcallback) is now deprecated. Use [`setVehicleCrashListener(VehicleCrashListener)`](../api-reference/android/sentiance.md#setvehiclecrashlistener) instead.

#### Fixed

* Minor stability and timeline quality improvements.

## \[4.16.2\] - 2 Jul 2020

#### Fixed

* Fatal exception when aborting service start-up due to uninitialized SDK.

## \[4.16.1\] - 19 Jun 2020

#### Fixed

* Stability improvement in the SDK logging subsystem.

## \[4.16.0\] - 3 Jun 2020

{% hint style="info" %}
Starting from 4.16.0, SDK detections will no longer be supported on Android 4.4 and lower. When initializing the SDK, [`onInitFailure`](../api-reference/android/oninitcallback/#oninitfailure) will return [`INITIALIZATION_ERROR`](../api-reference/android/oninitcallback/initissue.md) with an accompanying [`SdkException`](../api-reference/android/sdkexception.md) containing the message "Unsupported OS version."

This change does not impact the SDK's minimum supported API level \(i.e. minSdkVersion\).
{% endhint %}

#### Added

* Support for on-device trip profiling and hard event detection. This feature is not enabled by default.
* Support for remotely enabling "controlled trips only" detection mode.

#### Changed

* Disabled Proguard [method synchronization optimization](https://www.guardsquare.com/en/products/proguard/manual/usage/optimizations) \(method/marking/synchronized\) due to incorrect removal of `synchronized` method markings. This change is also carried over to any application code when using Proguard. If you're using R8, it will have no impact on your code.

#### Removed

* Detection support for Android 4.4. and lower is now disabled.
* The `WRITE_EXTERNAL_STORAGE` permission is no longer requested by the SDK. Previously, this permission was requested up to API level 18. If you rely on the presence of this permission in the final manifest, please add it manually to your app's manifest instead.

#### Fixed

* Issues related to ANR and failed foregrounding of SDK services.
* Properly reflect on the users timeline any SDK termination during trips.
* Ensure long trips are split to no more than 4 hour durations.
* Rare issue causing sensor timestamp misalignment.

## \[4.14.0\] - 31 Jan 2020

#### Added

* Support resetting the SDK to a "never initialized" state, clearing all SDK user data and allowing the creation of a new Sentiance user. See [`reset(ResetCallback)`](../api-reference/android/sentiance.md#reset).
* Improve the detection of granting the background location access permission on Android 10+. 

#### Changed

* Update and replace the use of deprecated Google Play Services APIs.

#### Fixed

* Motion activity detection issue during trips.
* A rare token refresh issue that causes an unreleased wakelock.
* Other minor bugs.

## \[4.13.0\] - 6 Jan 2020

{% hint style="info" %}
Starting from 4.13.0, we are no longer releasing the -R variant of the Sentiance SDK. If you are currently using the -R version, please update to the regular version. This change will not have any impact on your integration or user data.
{% endhint %}

#### **Changed**

* The `WRITE_EXTERNAL_STORAGE` manifest permission is now limited to API level 18 and lower.

#### Fixed

* Stop the internal heartbeat task when the SDK is stopped.
* Fix an occasional NullPointerException that occurs during detections.

## \[4.12.0\] - 4 Oct 2019

#### Removed

* The `ACCESS_BACKGROUND_LOCATION` permission is now removed from the SDK's manifest. If you are targeting API level 29+, please add this permission to your app's manifest instead. The inclusion of this permission affected apps targeting API level 28 or lower. For more information about this change, please see [here](../appendix/android/android-10-update-behavior.md).

## \[4.11.0\] - 23 Sep 2019

{% hint style="info" %}
This version targets API level 29, adding Android 10 support.
{% endhint %}

#### Added

* Android 10 permission support.
  * The `ACCESS_BACKGROUND_LOCATION` permission has been added to the SDK's manifest. Background location access is mandatory to support proper detections. See [Location Permission](../getting-started/android-sdk/permissions.md#location).
  * The `android.permission.ACTIVITY_RECOGNITION` permission is required on Android 10 and above to prevent degradation in the detection quality. See [Activity Recognition Permission](../getting-started/android-sdk/permissions.md#activity-recognition-android-10).
* Ability to obtain a user's nearby points of interest during stationary. You can now obtain a list of POIs and their type directly from the SDK instead of querying the Sentiance API. See [`getPointsOfInterest()`](../api-reference/android/stationaryinfo.md#getpointsofinterest).
* Report the app's notification setting \(enabled/disabled\) to the Sentiance Platform.
* Report the device's Google Play Services version to the Sentiance Platform.
* Keep a metadata journal to prevent sending duplicate user metadata requests.

#### Changed

* Target API level is now 29.
* Use Android's network capability API on Android 10.
* The return type of [`StationaryInfo.getLocation()`](../api-reference/android/stationaryinfo.md#getlocation) is no longer nullable. A stationary activity is guaranteed to have a proper location.

#### Fixed

* Rare crash caused by a null pointer exception during call detection.
* Rare crash caused by concurrent modification exception.
* Properly capture unhandled exceptions \(reported to the Sentiance Platform\).
* Incorrect [user activity type](../api-reference/android/useractivitytype.md) reported during SDK startup.

#### Security

* The Sentiance app secret is no longer stored by the SDK.

## \[4.10.1\] - 26 Aug 2019

#### Added

* Improved stationary detection.
* Faster detection of location permission grant.

#### Changed

* Decrease the number of notifications shown during stationary.
* Explicitly set the `uses-feature` "android.hardware.location.gps" `required` attribute to `false`.

#### Fixed

* Add missing fields to `toString()` and `equals()` methods of the [`SdkStatus`](../api-reference/android/sdkstatus/) class.
* Properly detect and end ongoing \(internal\) SDK trips with poor location accuracy.

## \[4.10.0\] - 24 Jun 2019

#### Added

* Support automatic stopping of detections by specifying an expiry date when calling [`start()`](../api-reference/android/sentiance.md#start-1). The expired detection will cause the [`StartStatus`](../api-reference/android/sdkstatus/startstatus.md) to become `START_EXPIRED`.
* Support additional fine-tuning of the SDK's disk usage quota.

#### Fixed

* Rare crash caused by a NullPointerException in the ContinuousSensorStreamService class.

## \[4.9.1\] - 6 Jun 2019

#### Added

* Remotely configurable sensor collection rate for non -R SDK versions.

#### Changed

* Relax the high accuracy location mode requirement. Detections will also work with battery saving mode.

#### Fixed

* Occasional excessive wake-ups on Samsung devices.
* Rare issue where duplicate detection payloads are uploaded to the server.
* Rare issue where an invalid waypoint is added to a trip.

## \[4.9.0\] - 21 May 2019

#### Added

* Support adding trip metadata during an ongoing trip. See [`addTripMetadata()`](../api-reference/android/sentiance.md#addtripmetadata).
* Support asynchronous user linking. See [`setMetaUserLinker()`](../api-reference/android/sdkconfig/sdkconfig-builder.md#setmetauserlinker-1).
* Send user-agent info to API calls.

#### Changed

* Internal changes to user linking, sdk configuration updates, and SDK heartbeat data.

#### Fixed

* Issue related to incorrectly timed activity transition events supplied by play services.

## \[4.8.0\] - 24 Apr 2019

#### Added

* Batched payload submission.
* Voip call detection.

#### Changed

* Improved trip detection.

#### Fixed

* Screen on/off detection during trips.

## \[4.7.1\] - 3 Apr 2019

#### Fixed

* Deobfuscate [`TripInfo`](../api-reference/android/tripinfo.md) and [`StationaryInfo`](../api-reference/android/stationaryinfo.md) classes used with [`UserActivity`](../api-reference/android/useractivity.md).
* Fix crash when targeting a pre-12.0.1 version of Google Play Location Services.
* Minor internal bug fixes and improvements.

## \[4.7.0\] - 25 Mar 2019

#### Added

* Support updating the SDK notification at runtime with [`updateSdkNotification(Notification)`](../api-reference/android/sentiance.md#updatesdknotification).
* Ability to register for user activity updates \(trips and stationary moments\) with [`setUserActivityListener(UserActivityListener)`](../api-reference/android/sentiance.md#setuseractivitylistener).

#### Fixed

* Fixed a rare issue where the location availability sdk status value is incorrect.
* Other minor bugs.

## \[4.6.0\] - 13 Mar 2019

#### Added

* Support overwriting the Sentiance API URL with [`SdkConfig.Builder.baseURL(String)`](../api-reference/android/sdkconfig/sdkconfig-builder.md#baseurl).
* App version code in the device info payload.

#### Fixed

* Prevent creating very long stationaries when the device has been offline \(no location updates or powered off\).

## \[4.5.2\] - 4 Mar 2019

#### Changed

* Include geofence exit triggering locations in trips.
* Drop payloads when the API responds with 413 \(payload too large\).
* Reschedule SDK tasks with changed criteria.

#### Fixed

* Rare crash caused by shared SimpleDateFormat instance.
* Prevent stopping of incoming location fixes during trips caused by high frequency requests \(1 per 10 secs or higher\).

## \[4.5.1\] - 20 Feb 2019

#### Added

* Capture unexpected exceptions and errors during SDK init, and fail with reason [`InitIssue.INITIALIZATION_ERROR`](../api-reference/android/oninitcallback/initissue.md).
* Minor detection improvement.

#### Changed

* [`OnInitCallback.onInitFailure()`](../api-reference/android/oninitcallback/#oninitfailure) now passes a [`Throwable`](https://developer.android.com/reference/java/lang/Throwable) as an additional parameter in case of the aforementioned [`InitIssue.INITIALIZATION_ERROR` ](../api-reference/android/oninitcallback/initissue.md).

#### Fixed

* Stuck stationary issue.
* Alarms not triggering on Samsung.

## \[4.5.0\] - 11 Feb 2019

#### Added

* Upload device location-mode, battery-saving state, and battery optimization config to the Sentiance platform.
* Capture hourly heartbeat events to track SDK runtime.
* Support uploading select SDK events \(e.g. heartbeat\) to the Sentiance platform over mobile data.

#### Fixed

* [`TransportMode`](../api-reference/android/trip/transportmode.md) enum obfuscation issue.

## \[4.4.0\] - 17 Jan 2019

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

## \[4.3.0\] - 9 Jan 2019

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

## \[4.2.9\] - 18 Dec 2018

#### Added

* `android.permission.FOREGROUND_SERVICE` permission required for Android 9.

#### Changed

* Updated target API to 28.

#### Fixed

* Bug fixes.

## \[4.2.8\] - 21 Nov 2018

#### Changed

* Improved detection algorithm.

## \[4.2.7\] - 15 Nov 2018

#### Fixed

* Bug fixes.

## \[4.2.6\] - 12 Nov 2018

#### Added

* Support for sending mocked locations.

#### Changed

* Improved detection algorithm.

#### Fixed

* Minor bug fixes.

## \[4.2.5\] - 22 Oct 2018

#### Added

* Provide the ability to set the SDK's notification ID.

#### Changed

* Improve stationary detection.

#### Fixed

* Fix google play console warning related to AWS credentials.

## \[4.2.4\] - 8 Oct 2018

#### Changed

* Disable SDK notifications for triggered trips flavor when no trip is ongoing.

#### Fixed

* Prevent LocationService from crashing during startup.

## \[4.2.3\] - 2 Oct 2018

#### Changed

* Stationary detection improvement.

## \[4.2.1\] - 24 Sep 2018

#### Added

* More SDK logging.

#### Changed

* Removed explicit allowBackup param from manifest.

#### Fixed

* Wakelock prevention and other minor fixes.

## \[4.2.0\] - 27 Aug 2018

#### Added

* Support for meta users.
* Remotely configurable required location providers.

## \[4.1.22\] - 23 Aug 2018

#### Fixed

* Prevent automatic detections in triggered trips mode.

## \[4.1.21\] - 21 Aug 2018

#### Changed

* Location parameter of `CrashCallback.onCrash()` is now nullable.
* Vehicle crash detection algorithm update.

#### Fixed

* Various bug fixes.

