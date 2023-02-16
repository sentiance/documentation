# Android

## \[6.2.3] - 16 Feb 2023

#### Fixed

* Runtime exception when retrieving historic app exit reasons, as a result of buggy Android framework code on some Samsung devices.

## \[6.1.1] - 3 Feb 2023

{% hint style="info" %}
This patched version should be used only if you intend to remain on version 6.1. Otherwise, it is recommended to use the latest 6.2 version instead.
{% endhint %}

#### Fixed

* A stability issue in v6.1.0 impacting http requests.

## \[6.2.2] - 31 Jan 2023

#### Added

* Proguard rules for Google Play Service Location library classes, which are required since SDK v6.2.1.

## \[6.2.1] - 19 Jan 2023

#### Fixed

* Runtime exception when targeting Google Play Services Location library v21.

## \[6.2.0] - 9 Jan 2023

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* Transport waypoint and distance information to [TransportEvent](../api-reference/android/usercontext/event/transportevent.md), which is part of the event list returned in [UserContext](../api-reference/android/usercontext/). Both waypoints and distance are based on unprocessed (i.e. raw) location data.
* User's current semantic time info to [UserContext](../api-reference/android/usercontext/) (e.g. morning, lunch, evening). See [SemanticTime](../api-reference/android/usercontext/segmenttype.md).
* Support for uploading additional SDK status information to the Sentiance Cloud Platform.
* New SDK dependencies. See [dependencies](../appendix/android/artifacts-dependencies.md).

#### Changed

* Stationary venue mapping has been update to an improved version, but that is limited to venue-type mapping. i.e. a stationary will no longer reference a specific venue, but a venue type instead.
* Improved support for on-device user segment detection.
* The Android target and compile API versions have been updated to 33.
* Improved detection of delayed SDK initialization.

#### Fixed

* IllegalArgumentException caused by inconsistency during sorting a collection.
* ForegroundServiceStartNotAllowedException when starting a service in the background.
* NullPointerException when uploading logs to the Sentiance Cloud Platform.

#### Removed

* BREAKING: _UserContextUpdateCriteria.ACTIVE\_MOMENTS_.
* BREAKING: The _Moment_ class. _UserContext_ no longer returns moments.
* BREAKING: _venueSignificance_ is removed from _StationaryEvent_, and moved to the _Venue_ class. _StationaryEvent_ now references a _Venue_.
* BREAKING: _VenueCandidates_ and _Visit_ classes are removed. _venueCandidates_ has been removed from _StationaryEvent_.
* BREAKING: _Venue_ now has a nullable location, which previously was not nullable. The location can be null when it's unknown, such as when a stationary has a venue significance of "point of interest". In this case, only the venue type is known, but not its exact location.
* BREAKING: _Venue_ no longer has venue name or labels.

## \[6.1.0] - 30 Sep 2022 (Unpublished. Use 6.1.1)

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* Diagnostic API for monitoring vehicle crash detection. See [setVehicleCrashDiagnosticListener](../api-reference/android/crashdetectionapi.md#setvehiclecrashlistener).
* App-configurable rules to control SDK data transmission to the Sentiance Cloud Platform. The app can specify which of the following data types are allowed to be transmitted to the Sentiance platform: vehicle crash data, SDK and device info, general detection data, all data. See [setTransmittableDataTypes](../api-reference/android/sentiance.md.md#settransmittabledatatypes).
* Support for car, bus, train, and tram/metro transport mode detection, part of the user's current context information.
* Internal support in the SDK to notify the Sentiance Cloud Platform that the SDK has been reset.

#### Changed

* Improved the detection of user device interaction during trips.
* Improved the error details that is returned to the app during failed user creation.

#### Fixed

* Detection of vehicle crashes that occur towards the end of a trip.

#### Removed

* BREAKING: _vehicle_ and _rail_ [transport modes](../api-reference/android/usercontext/event/transportmode.md) from the user's current context information.

## \[6.0.2] - 30 Aug 2022

#### Changed

* Improved the vehicle crash detection algorithm.

## \[4.22.2] - 30 Aug 2022

#### Changed

* Improved the vehicle crash detection algorithm.

## \[6.0.1] - 16 Aug 2022

#### Fixed

* Failure to reset the SDK, when the SDK hasn't been initialized yet.
* Invalid SDK state, when user creation is interrupted by app termination or unfinished user linking, requiring an SDK reset to be able to complete user creation.

## \[6.0.0] - 1 Aug 2022

{% hint style="info" %}
**Breaking Changes**

Version 6.0 is a major release and includes multiple deprecations and breaking changes. Please read our [migration guide](../appendix/migration-guide/android.md#migrating-from-4-x-to-6-x) to learn how to upgrade to this version.

Given the significance of the changes in this version, we recommend testing your app carefully, before making it available to your wider audience.
{% endhint %}

#### Added

* A Sentiance user creation method that supports the existing user-linking flow, and a new authentication-code based flow. The new flow is the recommended approach for future integrations.
* A dedicated SDK initializer that does not create a Sentiance user. To be used in combination with the user creation method.
* Improved versions of asynchronous SDK methods that return `PendingOperation` as a result (akin to a Java Future), instead of accepting success/failure callbacks, offering more flexibility and Kotlin friendliness.
* Detection enabling and disabling methods that are persistent across app restarts, and that replace the SDK's start and stop methods.
* `CrashDetectionApi` for accessing and subscribing for vehicle crash detection info. This class is in the newly added _com.sentiance.sdk-crash-detection_ artifact.
* User Context information, which can be requested or subscribed for, and which includes a user's recent timeline events, the home and work locations (if detected), and a user's segments (if detected). This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. For more information about it, see our [On-Device Features page](../appendix/on-device-features.md).
* On-device user event timeline generation, with support for real-time transport classification using Sentiance's ML-based transport classifier. This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. The timeline is made available via the _UserContextApi_ class.
* On-device venue mapping of stationary locations, using Sentiance's ML-based classifier. This feature uses venue data that is downloaded and stored offline. It is released as [Early Access](../appendix/feature-production-readiness.md). The venue information is made available via the _UserContextApi_ class. For more information about this feature, see our [On-Device Features page](../appendix/on-device-features.md).
* On-device [segment](../../library/segments.md) detection. This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. The segment data is made available via the _UserContextApi_ class. For more information about this feature, see our [On-Device Features page](../appendix/on-device-features.md).
* Ability to capture mini-dumps of native process crashes.
* Ability to capture ANR data for troubleshooting on Android 11+.
* Limited support for running detections when the location permission is _while-in-use_, and when the app is in the foreground.
* Support for collecting various sensor data when the app is in the foreground.
* Nullability annotations for all public methods and classes.
* `SdkStatus.userExists` and `SdkStatus.detectionStatus`
* `userExists` and `isUserLinked` methods in the `Sentiance` class, accessible without initializing the SDK.

#### Changed

* Bumped the minimum support Android version to 6.0.
* Required target Java language level is Java 8.
* Switched to the R8 obfuscator/shrinker.
* Switched to a modular artifact architecture. Some features are not extracted to their own modules. e.g. Crash detection is now in the _com.sentiance:sdk-crash-detection_ artifact, which must be added separately to your app.
* Vehicle crash detection functionality has been moved to the artifact _com.sentiance:sdk-crash-detection_. Related methods and classes have been moved to a different package.
* `MetaUserLinker` is renamed to `UserLinker`.
* `MetaUserLinkerAsync` is renamed to `UserLinkerAsync`.
* `MetaUserLinkerCallback` is renamed to `UserLinkerCallback`.
* `SdkConfig.Builder.setMetaUserLinker()` is renamed to `SdkConfig.Builder.setUserLinker()`
* Moved the following methods and classes to new package: `invokeDummyVehicleCrash`, `setVehicleCrashListener`, `isVehicleCrashDetectionSupported`, `VehicleCrashEvent`, `VehicleCrashListener`

#### Deprecated

* `init(SdkConfig, OnInitCallback)`
* `reset(ResetCallback)`
* `start(OnStartFinishedHandler),` `start(Date, OnStartFinishedHandler)` and `stop()`
* `getUserAccessToken(TokenResultCallback)`
* `startTrip(Map<String, String>,TransportMode, StartTripCallback)` and `stopTrip(StopTripCallback)`
* `submitDetections(SubmitDetectionsCallback)`
* `SdkStatus.startStatus` and `SdkStatus.locationPermission`

#### Fixed

* Occasional ANR events caused by the SDK during start.

#### Removed

* Proguard rule `-keepattributes SourceFile, LineNumberTable`
* `setCrashCallback(CrashCallback)` and `CrashCallback`
* `isInitialized()`
* `SdkConfig.isForegroundEnabled()`
* `TripProfileConfig`, `TripProfileListener`, `setTripProfileListener(TripProfileListener)`, and `updateTripProfileConfig(TripProfileConfig)`
* `SdkStatus.isLocationPermGranted`

## \[4.22.1] - 04 July 2022

#### Changed

* Improved the vehicle crash detection algorithm.

## \[4.22.0] - 30 May 2022

{% hint style="info" %}
This release updates the SDK's TensorFlow Lite dependency version to 2.7.0. If your app depends on a different version of TensorFlow Lite, make sure to test it for compatibility before updating.
{% endhint %}

#### Changed

* Updated the TensorFlow Lite dependency to v2.7.0.
* Updated the vehicle crash detection ML model for TensorFlow Lite v2.7.0 compatibility.

## \[4.21.3] - 27 Apr 2022

#### Changed

* Improved the vehicle crash detection algorithm.

## \[4.21.2] - 25 Mar 2022

#### Fixed

* A minor bug in the cash detector related to processing negative longitude and latitude coordinates.

## \[4.21.0] - 3 Feb 2022

#### Added

* Step count tracking (disabled by default).

#### Changed

* Improved the vehicle crash detection algorithm.
* Added support for vehicle crash detection when activity recognition permission is not granted.
* Improved trip detection under certain inaccurate location conditions.
* Added more leniency towards short interruptions to the SDK detections that are caused by toggled airplane mode, or changing of available location providers (usually a result of OS power saving optimizations).
* Limited foregrounding SDK services when the debugger is attached, to prevent potential ANRs.

#### Deprecated

* Legacy on-device trip profiling. This feature will be removed in the next major release.

#### Fixed

* Incompatible machine learning model usage when the SDK is downgraded.
* SecurityException on Android 5 when the READ\_PHONE\_STATE permission is missing.

#### Security

* Avoid logging credentials in the SDK's private log files.

## \[4.20.0] - 7 Dec 2021

{% hint style="info" %}
This version targets API level 31, adding Android 12 support.
{% endhint %}

{% hint style="warning" %}
If you app supports Android 5, you must add the _READ\_PHONE\_STATE_ permission in your app's manifest in order to allow the Sentiance SDK to detect phone calls. You can limit this permission to API level 22 by specifying _android:maxSdkVersion="22"_.

Note: the absence of _READ\_PHONE\_STATE_ in your app's manifest will cause the application to crash on Android 5. This is a bug that will be fixed in the next SDK version.
{% endhint %}

#### Added

* Support for targeting Android 12 in the host app.
* HIGH\_SAMPLING\_RATE\_SENSORS manifest permission for Android 12.
* SCHEDULE\_EXACT\_ALARM manifest permission for Android 12.
* ACCESS\_COARSE\_LOCATION manifest permission for Android 12.

#### Changed

* Improved crash detection with an update to the internal crash detection model.
* Exported all manifest components that define intent filters.
* Specified mutability for internal Pending Intents.
* Updated mobile call detection to work without requiring the READ\_PHONE\_STATE permission (on Android 6 and above).
* Modified foreground service usage to support the new Android 12 restriction.
* Handled the absence of the precise location permission. The SDK will stop detections if this permission (ACCESS\_FINE\_LOCATION) is not granted. A new status indicator called **isPreciseLocationPermGranted** has been added to the **SdkStatus** for this purpose.
* Reduced the number of Android notifications that appear during stationary.

#### Fixed

* NullPointerException caused by **JobScheduler.getAllPendingJobs()** returning null in some instances.
* Memory leak cause by holding a strong reference to an SDK service instance.

#### Removed

* The READ\_PHONE\_STATE permission has been removed from SDK library manifest. This permission was previously capped at API level 22, using the **maxSdkVersion** attribute.

## \[4.19.3] - 14 Sep 2021

#### Fixed <a href="#markdown-header-added" id="markdown-header-added"></a>

* Occasional SecurityException when accessing the ConnectivityManager on Android 11+ devices.
* Failure to detect some phone calls during trips.
* A rare occurrence of a NullPointerException during internal SDK message handling.

## \[4.19.2] - 1 Jul 2021

#### Fixed <a href="#markdown-header-added" id="markdown-header-added"></a>

* Failure to initialize the SDK on some emulator images due to a divide by zero error.

## \[4.19.1] - 9 Jun 2021

#### Fixed <a href="#markdown-header-added" id="markdown-header-added"></a>

* Failure to run crash detection immediately after resetting the SDK.

## \[4.19.0] - 14 Apr 2021

#### Added <a href="#markdown-header-added" id="markdown-header-added"></a>

* Support for tracking app foreground and background state changes.
* Support for collecting accelerometer range and max supported frequency.
* Improve detection of tablet devices by taking the device's smallest screen width into account.

**Changed**

* Use existing authentication token when submitting a token refresh request.
* Add fail-fast mechanism during third party user linking if linking has not been completed.

#### Fixed <a href="#markdown-header-fixed" id="markdown-header-fixed"></a>

* Improve handling of out of order sensor data
* Fix skipped events in some rare cases.

## \[4.18.1] - 8 Feb 2021

#### Fixed

* Stability improvements to the user authentication and sensor data collection.

## \[4.18.0] - 14 Jan 2021

#### Added

* An improved and a more accurate vehicle crash detection, backed by a machine learning model. You must switch to using the new Sentiance API method [`setVehicleCrashListener(VehicleCrashListener)`](broken-reference) to activate it.
* A new method to help test your crash detection integration. See [`invokeDummyCrash()`](broken-reference).
* A new method to check if crash detection is supported on the device for a specific trip type. See [`isCrashDetectionSupported(TripType)`](broken-reference).

#### Changed

* Points of interest data is no longer provided in the [`StationaryInfo`](../api-reference/android/stationaryinfo.md) object (returned by [`getStationaryInfo()`](../api-reference/android/useractivity.md#getstationaryinfo)) by default. If you use this data, please reach out to us before updating to this SDK version.
* On Android 9 and above, when [background execution is restricted](https://developer.android.com/reference/android/app/ActivityManager#isBackgroundRestricted\(\)) for your app (by the user or an OS power saving feature), SDK detections will no longer run. An [`SdkStatus`](../api-reference/android/sdkstatus/) update will be delivered to your app, with `startStatus` set to `PENDING` and `isBackgroundProcessingRestricted` set to `true` so that you can take the appropriate action.
* Library dependency changes:
  * Removed compile-time dependency on `com.google.code.findbugs:jsr305`
  * Added runtime dependency on `org.tensorflow:tensorflow-lite:2.2.0`. This dependency adds native libraries to your app. To limit their architectures, see [here](../troubleshooting/android.md#exclude-native-libraries-for-unsupported-architectures).

#### Deprecated

* &#x20;[`setCrashCallback(CrashCallback)`](broken-reference) is now deprecated. Use [`setVehicleCrashListener(VehicleCrashListener)`](broken-reference) instead.

#### Fixed

* Minor stability and timeline quality improvements.

## \[4.16.2] - 2 Jul 2020

#### Fixed

* Fatal exception when aborting service start-up due to uninitialized SDK.

## \[4.16.1] - 19 Jun 2020

#### Fixed

* Stability improvement in the SDK logging subsystem.

## \[4.16.0] - 3 Jun 2020

{% hint style="info" %}
Starting from 4.16.0, SDK detections will no longer be supported on Android 4.4 and lower. When initializing the SDK, [`onInitFailure`](../api-reference/android/oninitcallback/#oninitfailure) will return [`INITIALIZATION_ERROR`](../api-reference/android/oninitcallback/initissue.md) with an accompanying [`SdkException`](../api-reference/android/sdkexception.md) containing the message "Unsupported OS version."

This change does not impact the SDK's minimum supported API level (i.e. minSdkVersion).
{% endhint %}

#### Added

* Support for on-device trip profiling and hard event detection. This feature is not enabled by default.
* Support for remotely enabling "controlled trips only" detection mode.

#### Changed

* Disabled Proguard [method synchronization optimization](https://www.guardsquare.com/en/products/proguard/manual/usage/optimizations) (method/marking/synchronized) due to incorrect removal of `synchronized` method markings. This change is also carried over to any application code when using Proguard. If you're using R8, it will have no impact on your code.

#### Removed

* Detection support for Android 4.4. and lower is now disabled.
* The `WRITE_EXTERNAL_STORAGE` permission is no longer requested by the SDK. Previously, this permission was requested up to API level 18. If you rely on the presence of this permission in the final manifest, please add it manually to your app's manifest instead.

#### Fixed

* Issues related to ANR and failed foregrounding of SDK services.
* Properly reflect on the users timeline any SDK termination during trips.
* Ensure long trips are split to no more than 4 hour durations.
* Rare issue causing sensor timestamp misalignment.

## \[4.14.0] - 31 Jan 2020

#### Added

* Support resetting the SDK to a "never initialized" state, clearing all SDK user data and allowing the creation of a new Sentiance user. See [`reset(ResetCallback)`](broken-reference).
* Improve the detection of granting the background location access permission on Android 10+.&#x20;

#### Changed

* Update and replace the use of deprecated Google Play Services APIs.

#### Fixed

* Motion activity detection issue during trips.
* A rare token refresh issue that causes an unreleased wakelock.
* Other minor bugs.

## \[4.13.0] - 6 Jan 2020

{% hint style="info" %}
Starting from 4.13.0, we are no longer releasing the -R variant of the Sentiance SDK. If you are currently using the -R version, please update to the regular version. This change will not have any impact on your integration or user data.
{% endhint %}

#### **Changed**

* The `WRITE_EXTERNAL_STORAGE` manifest permission is now limited to API level 18 and lower.

#### Fixed

* Stop the internal heartbeat task when the SDK is stopped.
* Fix an occasional NullPointerException that occurs during detections.

## \[4.12.0] - 4 Oct 2019

#### Removed

* The `ACCESS_BACKGROUND_LOCATION` permission is now removed from the SDK's manifest. If you are targeting API level 29+, please add this permission to your app's manifest instead. The inclusion of this permission affected apps targeting API level 28 or lower. For more information about this change, please see [here](../appendix/android/android-10-update-behavior.md).

## \[4.11.0] - 23 Sep 2019

{% hint style="info" %}
This version targets API level 29, adding Android 10 support.
{% endhint %}

#### Added

* Android 10 permission support.
  * The `ACCESS_BACKGROUND_LOCATION` permission has been added to the SDK's manifest. Background location access is mandatory to support proper detections. See [Location Permission](../getting-started/android-sdk/permissions.md#location).
  * The `android.permission.ACTIVITY_RECOGNITION` permission is required on Android 10 and above to prevent degradation in the detection quality. See [Activity Recognition Permission](../getting-started/android-sdk/permissions.md#activity-recognition-android-10).
* Ability to obtain a user's nearby points of interest during stationary. You can now obtain a list of POIs and their type directly from the SDK instead of querying the Sentiance API. See [`getPointsOfInterest()`](../api-reference/android/stationaryinfo.md#getpointsofinterest).
* Report the app's notification setting (enabled/disabled) to the Sentiance Platform.
* Report the device's Google Play Services version to the Sentiance Platform.
* Keep a metadata journal to prevent sending duplicate user metadata requests.

#### Changed

* Target API level is now 29.
* Use Android's network capability API on Android 10.
* The return type of [`StationaryInfo.getLocation()`](../api-reference/android/stationaryinfo.md#getlocation) is no longer nullable. A stationary activity is guaranteed to have a proper location.

#### Fixed

* Rare crash caused by a null pointer exception during call detection.
* Rare crash caused by concurrent modification exception.
* Properly capture unhandled exceptions (reported to the Sentiance Platform).
* Incorrect [user activity type](../api-reference/android/useractivitytype.md) reported during SDK startup.

#### Security

* The Sentiance app secret is no longer stored by the SDK.

## \[4.10.1] - 26 Aug 2019

#### Added

* Improved stationary detection.
* Faster detection of location permission grant.

#### Changed

* Decrease the number of notifications shown during stationary.
* Explicitly set the `uses-feature` "android.hardware.location.gps" `required` attribute to `false`.

#### Fixed

* Add missing fields to `toString()` and `equals()` methods of the [`SdkStatus`](../api-reference/android/sdkstatus/) class.
* Properly detect and end ongoing (internal) SDK trips with poor location accuracy.

## \[4.10.0] - 24 Jun 2019

#### Added

* Support automatic stopping of detections by specifying an expiry date when calling [`start()`](broken-reference). The expired detection will cause the [`StartStatus`](../api-reference/android/sdkstatus/startstatus.md) to become `START_EXPIRED`.
* Support additional fine-tuning of the SDK's disk usage quota.

#### Fixed

* Rare crash caused by a NullPointerException in the ContinuousSensorStreamService class.

## \[4.9.1] - 6 Jun 2019

#### Added

* Remotely configurable sensor collection rate for non -R SDK versions.

#### Changed

* Relax the high accuracy location mode requirement. Detections will also work with battery saving mode.

#### Fixed

* Occasional excessive wake-ups on Samsung devices.
* Rare issue where duplicate detection payloads are uploaded to the server.
* Rare issue where an invalid waypoint is added to a trip.

## \[4.9.0] - 21 May 2019

#### Added

* Support adding trip metadata during an ongoing trip. See [`addTripMetadata()`](broken-reference).
* Support asynchronous user linking. See [`setMetaUserLinker()`](../api-reference/android/sdkconfig/sdkconfig-builder.md#setmetauserlinker-1).
* Send user-agent info to API calls.

#### Changed

* Internal changes to user linking, sdk configuration updates, and SDK heartbeat data.

#### Fixed

* Issue related to incorrectly timed activity transition events supplied by play services.

## \[4.8.0] - 24 Apr 2019

#### Added

* Batched payload submission.
* Voip call detection.

#### Changed

* Improved trip detection.

#### Fixed

* Screen on/off detection during trips.

## \[4.7.1] - 3 Apr 2019

#### Fixed

* Deobfuscate [`TripInfo`](../api-reference/android/tripinfo.md) and [`StationaryInfo`](../api-reference/android/stationaryinfo.md) classes used with [`UserActivity`](../api-reference/android/useractivity.md).
* Fix crash when targeting a pre-12.0.1 version of Google Play Location Services.
* Minor internal bug fixes and improvements.

## \[4.7.0] - 25 Mar 2019

#### Added

* Support updating the SDK notification at runtime with [`updateSdkNotification(Notification)`](broken-reference).
* Ability to register for user activity updates (trips and stationary moments) with [`setUserActivityListener(UserActivityListener)`](broken-reference).

#### Fixed

* Fixed a rare issue where the location availability sdk status value is incorrect.
* Other minor bugs.

## \[4.6.0] - 13 Mar 2019

#### Added

* Support overwriting the Sentiance API URL with [`SdkConfig.Builder.baseURL(String)`](../api-reference/android/sdkconfig/sdkconfig-builder.md#baseurl).
* App version code in the device info payload.

#### Fixed

* Prevent creating very long stationaries when the device has been offline (no location updates or powered off).

## \[4.5.2] - 4 Mar 2019

#### Changed

* Include geofence exit triggering locations in trips.
* Drop payloads when the API responds with 413 (payload too large).
* Reschedule SDK tasks with changed criteria.

#### Fixed

* Rare crash caused by shared SimpleDateFormat instance.
* Prevent stopping of incoming location fixes during trips caused by high frequency requests (1 per 10 secs or higher).

## \[4.5.1] - 20 Feb 2019

#### Added

* Capture unexpected exceptions and errors during SDK init, and fail with reason [`InitIssue.INITIALIZATION_ERROR`](../api-reference/android/oninitcallback/initissue.md).
* Minor detection improvement.

#### Changed

* [`OnInitCallback.onInitFailure()`](../api-reference/android/oninitcallback/#oninitfailure) now passes a [`Throwable`](https://developer.android.com/reference/java/lang/Throwable) as an additional parameter in case of the aforementioned [`InitIssue.INITIALIZATION_ERROR` ](../api-reference/android/oninitcallback/initissue.md).

#### Fixed

* Stuck stationary issue.
* Alarms not triggering on Samsung.

## \[4.5.0] - 11 Feb 2019

#### Added

* Upload device location-mode, battery-saving state, and battery optimization config to the Sentiance platform.
* Capture hourly heartbeat events to track SDK runtime.
* Support uploading select SDK events (e.g. heartbeat) to the Sentiance platform over mobile data.

#### Fixed

* [`TransportMode`](../api-reference/android/trip/transportmode.md) enum obfuscation issue.

## \[4.4.0] - 17 Jan 2019

#### Added

* Support for uploading SDK logs over mobile data.
* Detection improvements to some Samsung and Huawei devices.

#### Changed

* Prevent Sentiance credentials change for an already authenticated user (init will fail with [`CHANGED_CREDENTIALS`](../api-reference/android/initstate.md)).
* Prevent premature user access token refreshes.

#### Deprecated

* `Sentiance.isInitialized()` is now deprecated. Use [`Sentiance.getInitState()`](broken-reference) instead, which returns an [`InitState`](../api-reference/android/initstate.md) enum.

#### Fixed

* Minor bug fixes.

## \[4.3.0] - 9 Jan 2019

#### Added

* Ability to disable battery optimization for improved detections (see [here](../appendix/android/android-battery-optimization.md)).
* New [`SdkStatus`](../api-reference/android/sdkstatus/) fields.
  * `isBatteryOptimizationEnabled`
  * `isBatterySavingEnabled`
  * `isBackgroundProcessingRestricted`

#### Changed

* Updated min required Google Play Location Services version to 12.0.1.
* Improved detections.

#### Fixed

* Minor bug fixes.

## \[4.2.9] - 18 Dec 2018

#### Added

* `android.permission.FOREGROUND_SERVICE` permission required for Android 9.

#### Changed

* Updated target API to 28.

#### Fixed

* Bug fixes.

## \[4.2.8] - 21 Nov 2018

#### Changed

* Improved detection algorithm.

## \[4.2.7] - 15 Nov 2018

#### Fixed

* Bug fixes.

## \[4.2.6] - 12 Nov 2018

#### Added

* Support for sending mocked locations.

#### Changed

* Improved detection algorithm.

#### Fixed

* Minor bug fixes.

## \[4.2.5] - 22 Oct 2018

#### Added

* Provide the ability to set the SDK's notification ID.

#### Changed

* Improve stationary detection.

#### Fixed

* Fix google play console warning related to AWS credentials.

## \[4.2.4] - 8 Oct 2018

#### Changed

* Disable SDK notifications for triggered trips flavor when no trip is ongoing.

#### Fixed

* Prevent LocationService from crashing during startup.

## \[4.2.3] - 2 Oct 2018

#### Changed

* Stationary detection improvement.

## \[4.2.1] - 24 Sep 2018

#### Added

* More SDK logging.

#### Changed

* Removed explicit allowBackup param from manifest.

#### Fixed

* Wakelock prevention and other minor fixes.

## \[4.2.0] - 27 Aug 2018

#### Added

* Support for meta users.
* Remotely configurable required location providers.

## \[4.1.22] - 23 Aug 2018

#### Fixed

* Prevent automatic detections in triggered trips mode.

## \[4.1.21] - 21 Aug 2018

#### Changed

* Location parameter of `CrashCallback.onCrash()` is now nullable.
* Vehicle crash detection algorithm update.

#### Fixed

* Various bug fixes.
