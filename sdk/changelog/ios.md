# iOS

## \[6.3.1] - 18 Apr 2023

#### Fixed

* Runtime exception when using the [TransportSession](../api-reference/ios/transport-sessions/senttransportsession.md) feature.
* A bug introduced in v6.3.0, which delayed the SDK's reaction to location permission changes.

## \[6.3.0] - 7 Apr 2023

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* A new Driving Insights feature, which provides information about a user's driving behaviour. In this first version, the SDK detects harsh driving events (e.g. acceleration, braking, and turning), which are then used to compute a vehicular transport's smooth driving score. This data is available via the new APIs in the Sentiance class, which allows the subscription to, and retrieval of [DrivingInsights](../api-reference/ios/driving-insights/sentdrivinginsights.md) and [HarshDrivingEvents](../api-reference/ios/driving-insights/sentharshdrivingevent.md). This feature must be enabled by Sentiance before use.
* New API methods in the Sentiance class which allow the subscription to, and retrieval of [TransportSessions](../api-reference/ios/transport-sessions/senttransportsession.md). A transport session corresponds to a transport that was detected by the SDK, and includes information such as the mode of transport, and the raw sensor data that was used to classify it. This API is primarily intended to be used for accessing the raw sensor data. To simply be notified of new transports, it's more efficient to utilize the [UserContext](../api-reference/ios/user-context/sentusercontext/) info.
* A short history of locations inside [SENTVehicleCrashEvent](../api-reference/ios/sentvehiclecrashevent.md), which represent the preceding locations leading up to the crash event.

#### Fixed

* Several minor stability issues.

#### Removed

* BREAKING: a number of [user segments](../api-reference/ios/user-context/sentsegment/sentsegmenttype.md) that are no longer supported.

## \[6.2.5] - 9 Mar 2023

#### Fixed

* [distanceInMeters](../api-reference/ios/user-context/senttimelineevent/senttransportevent.md#distanceinmeters) property of TransportEvent returns `nil` instead of a proper result.

## \[6.2.4] - 16 Feb 2023

#### Fixed

* Incorrect device low-power-mode indicator when checking the SDK status. This bug also impacted the system API result when calling `ProcessInfo.isLowPowerModeEnabled`.

## \[6.2.3] - 9 Feb 2023

#### Fixed

* An exception caused by deadlocking logic, when checking the background app refresh status and device thermal state.

## \[6.2.2] - 31 Jan 2023

#### Fixed

* An exception related to incompatible bundled models, caused by build-time SDK Bundle merge by Xcode.
* An issue where the SDK would start running in the background without detections being started, due to a conflict with a geofence set at the app level.
* An exception caused by deadlocking logic, when checking if the device is in low power mode.

## \[6.2.1] - 19 Jan 2023

#### Removed

* CocoaPods: `$(PODS_ROOT)/**` path from `SWIFT_INCLUDE_PATHS` that was being set by the SDK Podspec configuration. This was resulting in build errors when compiling Swift files.

#### Fixed

* High CPU usage when some on-device features were enabled, such as User Segment Detection and Stationary Venue-Type Mapping.

## \[6.2.0] - 9 Jan 2023

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* Transport waypoint and distance information to [SENTTransportEvent](../api-reference/ios/user-context/senttimelineevent/senttransportevent.md), which is part of the event list returned in [SENTUserContext](../api-reference/ios/user-context/sentusercontext/). Both waypoints and distance are based on unprocessed (i.e raw) location data.
* User's current semantic time info to [SENTUserContext](../api-reference/ios/user-context/sentusercontext/) (e.g. morning, lunch, evening). See [SENTSemanticTime](../api-reference/ios/user-context/sentsemantictime.md).
* A new multi-purpose SDK background task, with identifier `com.sentiance.backgroundtask.task_processing`_._ **Adding this identifier to your app's Info.plist is mandatory**. Please update your [project settings](../getting-started/ios-sdk/project-settings.md#setting-up-background-tasks), and enable Background fetch and processing capabilities.
* isDeviceLowPowerModeEnabled property to [SENTSDKStatus](../api-reference/ios/sentsdkstatus.md), to indicate whether the device is in low power mode.
* isMotionActivityPermissionGranted property to [SENTSDKStatus](../api-reference/ios/sentsdkstatus.md), to indicate whether the motion activity permission has been granted.
* Support for uploading additional SDK status information to the Sentiance Cloud Platform.
* New SDK dependency called dskoball. See [dependencies](../appendix/ios/dependencies.md).

#### Changed

* Stationary venue mapping has been update to an improved version, but that is limited to venue-type mapping. i.e. a stationary will no longer reference a specific venue, but a venue _type_ instead.
* Improved support for on-device user segment detection.
* The SDK's background task identifier _com.sentiance.backgroundtask.segment\_detection_ is no longer required. You may remove it from your app's Info.plist file.
* Disabled SDK logging to the device system log (i.e. console).

#### Fixed

* Rare exception when uploading logs to the Sentiance Cloud Platform.

#### Removed

* BREAKING: _SENTUserContextUpdateCriteriaActiveMoments criteria type._
* BREAKING: _SENTMoment_ class. _SENTUserContext_ no longer returns _moments_.
* BREAKING: _venueSignificance_ is removed from _SENTStationaryEvent_, and moved to _SENTVenue_. _SENTStationaryEvent_ now references a _SENTVenue_.
* BREAKING: SENTVenueCandidates and SENTVisit classes are removed. _venueCandidates_ has been removed from _SENTStationaryEvent_.
* BREAKING: _SENTVenue_ now has a nullable location, which previously was not nullable. The location can be nil when it's unknown, such as when a stationary has a venue significance of "point of interest". In this case, only the venue type is known, but not its exact location.
* BREAKING: _SENTVenue_ no longer has venue name or labels.

## \[6.1.3] - 1 Dec 2022

#### Fixed

* Runtime exception when processing a detected stationary for venue mapping purposes.

## \[6.1.2] - 24 Nov 2022

#### Fixed

* Missing vehicle crash information in the trip data that is uploaded to the Sentiance Platform.

## \[5.15.4] - 18 Nov 2022

#### Fixed

* An issue where the SDK continues detections after the location permission is downgraded to "while using the app."

## \[6.1.1] - 14 Nov 2022

#### Fixed

* Potential runtime exception related to the vehicle crash diagnostic feature.

## \[6.1.0] - 30 Sep 2022

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* Diagnostic API for monitoring vehicle crash detection. See [setVehicleCrashDiagnosticHandler:](../api-reference/ios/sentiance.md#setvehiclecrashdiagnostichandler)
* App-configurable rules to control SDK data transmission to the Sentiance Cloud Platform. The app can specify which of the following data types are allowed to be transmitted to the Sentiance platform: vehicle crash data, SDK and device info, general detection data, all data. See [setTransmittableDataTypes:](../api-reference/ios/sentiance.md#settransmittabledatatypes)
* Support for car, bus, train, and tram/metro transport mode detection, part of the user's current context information.
* Internal support in the SDK to notify the Sentiance Cloud Platform that the SDK has been reset.
* Support for specifying 'any' trip type when calling [isTripOngoing:](../api-reference/ios/sentiance.md#istripongoing) using SENTTripTypeAny.

#### Fixed

* Improve the detection of vehicle crashes that occur towards the end of a trip.
* Rare occurrence of a EXC\_BAD\_ACCESS crash.
* File operation exception at runtime, causing the process to crash.
* Inaccurate stationary venue information in some instances.

#### Removed

* BREAKING: _vehicle_ and _rail_ [transport modes](../api-reference/ios/user-context/senttimelinetransportmode.md) from the user's current context information.

## \[6.0.3] - 19 Sep 2022

#### Fixed

* Runtime exception when attempting to remove CLCircularRegions that were created by the SDK, while the app is also monitoring CLBeaconRegions.

## \[5.15.3] - 19 Sep 2022

#### Fixed

* Runtime exception when attempting to remove CLCircularRegions that were created by the SDK, while the app is also monitoring CLBeaconRegions.

## \[6.0.2] - 30 Aug 2022

{% hint style="info" %}
#### Swift Package Manager Support

Starting with this release, you can add the Sentiance SDK to your project as Swift Package. See [these](../getting-started/ios-sdk/include-sdk/using-swift-package-manager.md) instructions.
{% endhint %}

#### Changed

* Sentiance's [custom](../appendix/ios/m1-simulator-support.md) TensorFlowLiteC v2.7.0 XCFramework has been repackaged as a dynamic library framework. If you've integrated the SDK manually or by using Carthage, and will use the TensorFlowLiteC framework bundled in this release, make sure to update your project settings to embed and sign the TensorFlowLiteC framework. For other integration types, no changes are required.
* Improved the vehicle crash detection algorithm.

#### Fixed

* Occasional slow initialization while loading the SDK's resource bundle on some devices.
* Unterminated background processing and app refresh tasks, after the tasks have finished.
* Motion & Fitness permission dialog triggered by the SDK, when the step counting feature is activated.
* Optimized the download of venue data, used for on-device processing.
* An issue where a handler/listener that was set on the SDK would be lost after resetting the SDK.
* An issue where the SDK stops immediately after being initialized, when using the deprecated initializer.
* A rare issue where the main thread gets blocked while processing location data.

## \[5.15.2] - 30 Aug 2022

#### Changed

* Improved the vehicle crash detection algorithm.

## \[6.0.1] - 16 Aug 2022

#### Fixed

* Failure to update the deep learning crash detection model under certain circumstances, after an SDK update.
* Usage of incorrect trip-end location.
* Incorrectly returned NSDictionary as the user creation error detail, instead of an NSString.
* Invalid SDK state, when user creation is interrupted by app termination or unfinished user linking, requiring an SDK reset to be able to complete user creation.
* Failure to deliver SDK status updates when the location permission or precision changes.
* Blocking of the main thread during app startup, under rare circumstances.

## \[5.15.1] - 16 Aug 2022

#### Added

* Restored support for the armv7 architecture.

#### Fixed

* Failure to update the deep learning crash detection model under certain circumstances, after an SDK update.
* Usage of incorrect trip-end location.
* Rare stack overflow issue when submitting detections during SDK initialization.

## \[6.0.0] - 1 Aug 2022

{% hint style="info" %}
**Breaking Changes**

Version 6.0 is a major release and includes multiple deprecations and breaking changes. Please read our [migration guide](../appendix/migration-guide/ios.md) to learn how to upgrade to this version.

Given the significance of the changes in this version, we recommend testing your app carefully, before making it available to your wider audience.
{% endhint %}

#### Added

* A Sentiance user creation method that supports the existing user-linking flow, and a new authentication-code based flow. The new flow is the recommended approach for future integrations.
* A dedicated SDK initializer that does not create a Sentiance user. To be used in combination with the user creation method.
* Improved versions of asynchronous SDK methods that accept a result and error returning handler, offering more flexibility and Swift friendliness.
* Detection enabling and disabling methods that are persistent across app restarts, and that replace the SDK's start and stop methods.
* User Context information, which can be requested or subscribed for, and which includes a user's recent timeline events, the home and work locations (if detected), and a user's segments (if detected). This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. For more information about it, see our [On-Device Features page](../appendix/on-device-features.md).
* On-device user event timeline generation, with support for real-time transport classification using Sentiance's ML-based transport classifier. This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. The timeline is made available via the User Context data.
* On-device venue mapping of stationary locations, using Sentiance's ML-based classifier. This feature uses venue data that is downloaded and stored offline. It is released as [Early Access](../appendix/feature-production-readiness.md). The venue information is made available via the User Context. For more information about this feature, see our [On-Device Features page](../appendix/on-device-features.md).
* On-device [segment](../../library/segments.md) detection. This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. The segment data is made available via the User Context. For more information about this feature, see our [On-Device Features page](../appendix/on-device-features.md).
* Limited support for running detections when the location permission is _while-in-use_, and when the app is in the foreground.
* Nullability annotations for all public methods and classes.
* `SENTSDKStatus.userExists`, `SENTSDKStatus.backgroundRefreshStatus`, and `SENTSDKStatus.detectionStatus`
* `userExists` and `isUserLinked` methods in the `Sentiance` class, accessible without initializing the SDK.
* `isPreciseLocationAuthorizationGranted` to indicate whether precise location permission is granted.

#### Changed

* Bumped the minimum support iOS version to 13.0.
* The `SENTSDK` class has been renamed to `Sentiance`.
* Most `Sentiance` methods can no longer be called without initializing the SDK first. Exceptions are mentioned in each method's corresponding documentation.
* `MetaUserLinker` is renamed to `UserLinker`.
* `isVehicleCrashDetectionSupported` no longer accepts an argument..
* Modifications to `SENTConfig` after passing it to `initWithConfig:success:failure` are now ignored.

#### Deprecated

* `initWithConfig:success:failure:`
* `reset:failure:`
* `start:`, `startWithStopDate:completion:`, `stop`
* `getUserId`, `getUserActivity`, `getInitState`, `getSdkStatus`, `getVersion`, `getWifiQuotaLimit`, `getWiFiQuotaUsage`, `getMobileQuotaLimit`, `getMobileQuotaUsage`, `getDiskQuotaLimit`, `getDiskQuotaUsage` (deprecated in favor of properties).
* `getUserAccessToken:failure:`
* `startTrip:transportModeHint:success:failure` and `stopTrip:failure`
* `submitDetections:failure:`
* `SENTSDKStatus.startStatus` and `SENTSDKStatus.locationPermission`

#### Fixed

* Prevent blocking the main thread during startup under certain conditions.
* Improve the handling of false-trip detections.
* Stability fixes when resetting the SDK.
* OOM when uploading data to the Sentiance platform continuously fails.

#### Removed

* `setCrashListener:`
* `isInitialized`
* `setTripProfileHandler:`, `setFullTripProfilingEnabled:`, `setSpeedLimit:`&#x20;
* `SdkStatus.isLocationPermGranted`

## \[5.15.0] - 13 Jul 2022

#### Added

* Support for arm64 (M1 Mac) simulators. See [this guide](../appendix/ios/m1-simulator-support.md).

#### Changed

* The TensorFlowLiteC framework bundled in our fat framework and xcframework artifacts have been replaced with a custom TensorFlowLiteC v2.7.0 framework, which includes support for arm64 (device), arm64 (simulator), and x86\_64 (simulator) architectures.

#### Fixed

* Failure to clean up the keychain under certain circumstances, after app reinstallation. This resulted in restoring the previous Sentiance user on the device.
* Failure to run the vehicle crash detector when triggered-trips mode is enabled on the SDK.

#### Removed

* Support for armv7 (device) and i386 (simulator) architectures.

## \[5.14.1] - 4 Jul 2022

#### Added

* API to control background task identifier registration ([details](../api-reference/ios/sentconfig-1.md#registerbackgroundtaskidentifiers)). This is currently relevant only when the SDK's step-counter feature is being utilized.

#### Changed

* Improved the vehicle crash detection algorithm.

#### Fixed

* An issue that was introduced in v5.14.0, where iOS terminates the app when scheduling a background task. This was caused by the SDK registering background task identifiers outside of the app delegate.

## \[5.14.0] - 30 May 2022

{% hint style="info" %}
This release updates the SDK's TensorFlow Lite dependency version to 2.7.0. If your app depends on a different version of TensorFlow Lite, make sure to test it for compatibility before updating.
{% endhint %}

#### Changed

* Updated the TensorFlow Lite dependency to v2.7.0.
* Updated the vehicle crash detection ML model for TensorFlow Lite v2.7.0 compatibility.

## \[5.13.0] - 5 May 2022

#### Added

* Step count tracking (disabled by default).
* Support scheduling background tasks.

**Changed**

* Improved the vehicle crash detection algorithm.

## \[5.12.1] - 3 Feb 2022

#### Changed

* Improved the vehicle crash detection algorithm.
* Added support for vehicle crash detection when motion activity permission is not granted.

**Fixed**

* A bug that was introduced in v5.11.2, where reinstalling the app did not clear the previous Sentiance user.

## \[5.12.0] - 4 Jan 2022

#### Fixed

* Trip recording consistency upon unexpected app restart.
* Stability of background task usage in the SDK.
* Improved vehicle crash detection.
* Inability to detect trips after toggling the location precision setting on iOS 14+.

**Deprecated**

* Legacy on-device trip profiling. This feature will be removed in the next major release.

## \[5.11.2] - 8 Nov 2021

#### Fixed

* Fixed updating debug log configuration received from backstage.
* Removed obsolete linker flag '-all\_load' from podspec which lead to linker issues in recent react native environments.

## \[5.11.1] - 29 Jul 2021

#### Fixed

* Fixed an issue where detections were not able to start on iOS 15 devices due to the updated authorization status.
* Fixed TensorFLowLite model updating mechanism at runtime.
* Removed embedded TensorFlowLite library from SENTSDK pod by providing a separate thinned package and adding a pod dependency to TensorFlowLite (applies to CocoaPods integration only and requires CocoaPods 1.10.0 or above).

## \[5.11.0] - 16 Jul 2021

#### Added

* Support SDK artifacts without CallKit linkage&#x20;

#### Fixed

* Fixed rare and transient runtime crashes when object references inside the SDK get released from the OS due to erroneous reference semantics.
* Fixed delayed uploading of payloads in case of outdated authentication tokens.
* Fixed missing trip detections due to erroneous flip flop checks.

## \[5.10.1] - 20 May 2021

**Changed**

* Updated embedded TensorFlowLite framework to v2.4.0.

**Fixed**

* Fixed potential accelerometer data gaps in trip objects due to included data from previous trips.
* Fixed swift compiler warning since Xcode 12.5 wrt a missing include in the umbrella header.

## \[5.10.0] - 14 Apr 2021

#### Added <a href="#markdown-header-added" id="markdown-header-added"></a>

* Support for approximate location access available since iOS 14.
* Support for detection of screen lock/unlock events.

**Changed**

* Add fail-fast mechanism during third party user linking if linking has not been completed.
* Slightly adjust the actual stationary start time in the same way as the Android SDK.

#### Fixed <a href="#markdown-header-fixed" id="markdown-header-fixed"></a>

* Missing sensor data for crash events in some cases.
* Overlapping stationary events in case of trip timeouts.
* Recovery of trip object creation in case the SDK got killed by the OS.
* Trip object creation and submission in case of a crash event.

## \[5.9.0] -  29 Jan 2021

**Added**

* New type to SDK artifacts which are now packaged as both Framework and XCFramework (Please make sure to have CocoaPods 1.10.0 or above installed on your machine if you integrate Sentiance SDK via CocoaPods).
* An improved and more accurate vehicle crash detection, backed by a machine learning model. You must switch to using the new Sentiance API method [`setVehicleCrashHandler:`](../api-reference/ios/sentiance.md#setvehiclecrashhandler) to activate it.
* A new method to help test your crash detection integration. See [`invokeDummyVehicleCrash`](../api-reference/ios/sentiance.md#invokedummyvehiclecrashhandler).
* A new method to check if crash detection is supported on the device for a specific trip type. See [`isVehicleCrashDetectionSupported:`](../api-reference/ios/sentiance.md#isvehiclecrashdetectionsupported).

{% hint style="warning" %}
**Beta Feature:** Support for host apps that enable[ Data Protection](https://developer.apple.com/documentation/uikit/protecting\_the\_user\_s\_privacy/encrypting\_your\_app\_s\_files). This functionality is released as a beta feature and not yet recommended for production use.
{% endhint %}

**Changed**

* The trip serialization process utilizes a less intense and more optimized background processing model.

**Deprecated**

* [`setCrashListener:`](../api-reference/ios/sentiance.md#setcrashlistener) is now deprecated. Use [`setVehicleCrashHandler:`](../api-reference/ios/sentiance.md#setvehiclecrashhandler)instead.

**Fixed**

* An issue where portions of accelerometer and gyroscope data might be missed
* An issue where stationary detection might overlap with past stationary and trip detections
* An issue where the SDK might continuously report an initialization state of `SENTInitInProgress` after the initialization credentials are changed
* An issue where the SDK might continue collecting location fixes even after the user becomes stationary and cause excessive energy consumption
* An issue where the SDK might accidentally remove keychain items owned by the host app
* An issue where the SDK might crash during a network operation

**Removed**

* Location permission prompt when starting the SDK. If you rely on the SDK for prompting the user, please make sure you update your app and prompt the user during the onboarding.

## \[5.7.4] - 15 Jul 2020

#### Fixed

* The SQLCore I/O database error&#x20;
* High frequency GPS configuration

## \[5.7.3] - 9 Jul 2020

#### Fixed

* An issue where the SDK might not register geofences after determining that the user is stationary
* An issue where the SDK might use outdated geofences during stationary state determination

## \[5.7.1] - 4 Jun 2020

#### Fixed

* An issue when using beacon regions was causing unexpected exits

## \[5.7.0] - 3 Jun 2020

#### Added&#x20;

* Support added for on-device trip profiling and hard event detection.

## \[5.6.1] - 21 Feb 2020

**Fixed**

* An issue where the SDK might quit unexpectedly during resetting due to an internal issue

## \[5.6.0] - 5 Feb 2020

**Added**

* Support for [resetting](https://docs.sentiance.com/sdk/api-reference/ios/sentsdk#reset-failure) the SDK to factory settings, which clears all user data and allows creating a new Sentiance user**.**

**Changed**

* The geo-fence management policy so that the SDK does not intervene with the lifecycle of geo-fences owned by the enclosing app.
* Removed the motion activity permission prompt when starting the SDK. If you rely on the SDK for prompting the user, please make sure you update your app and prompt the user during the onboarding.

**Fixed**

* An issue where the SDK database might experience conflicts when the enclosing app also uses database instance(s) of CoreData.

## \[5.5.5] - 13 Nov 2019

* Fixed the SDK start/stop infinite loop when the user was selecting “Allow Once” for iOS 13 location permission.

## \[5.5.3] - 7 Oct 2019

**Fixed**

* _iOS 13_ background tasks crash
* Stuck in stationary (missing some trips)
* On base url change submission fix

## \[5.5.2] - 17 Sept 2019

#### Fixed

* _iOS 13_ crash fix
* Payload submission stability fixes

## \[5.5.1] - 27 Aug 2019

#### Added

* Support for [CocoaPods](https://cocoapods.org)
* [Integration Guide](broken-reference), to assist with installation and configuration of the SDK from Xcode

**Fixed**

* An issue that caused location observation to not stop properly when [`startWithStopDate:completion:`](https://docs.sentiance.com/sdk/api-reference/ios/sentsdk#startwithstopdate) is used

## \[5.4.0] - 2 Jul 2019

#### Added

* Method to [set stop date on SDK](../api-reference/ios/sentiance.md#startwithstopdate)
* new SENTStartStatus: [SENTStartStatusExpired](../api-reference/ios/sentsdkstatus.md#startstatus)

## \[5.3.2] - 14 Jun 2019

#### Added

* Method to set[ vehicle crash listener.](https://docs.sentiance.com/sdk/appendix/detecting-vehicle-crashes)

## \[5.3.0] - 4 Jun 2019

#### Added

* Method to set [user activity listener](../api-reference/ios/sentiance.md#setuseractivitylisterner).
* Method to get [current user activity](../api-reference/ios/sentiance.md#getuseractivity).

## \[5.2.1] - 29 May 2019

#### Added

* Method to [add metadata during](../api-reference/ios/sentiance.md#addtripmetadata) the trip.
* Method to [set base API](../api-reference/ios/sentconfig-1.md#baseurl) url for SDK.

#### Changed

* Stability and trip detection improvements.

#### Fixed

* Fix with reachability.

## \[5.1.8] - 28 Feb 2019

#### Changed

* Stability improvements.

## \[5.1.7] - 28 Jan 2019

#### Added

* Crash detection speed check.

#### Changed

* Improved trip start detection.
* Stability improvements.

## \[5.1.5] - 21 Dec 2018

#### Fixed

* iOS update fix
* Trip overlays on off the grid events
* Other fixes and improvements

## \[5.1.4] - 6 Nov 2018

#### Added

* Crash detection implemented

#### Fixed

* Fix with small amount of waypoints
* Trip duplication fix
* Other fixes and improvements

## \[5.1.3] - 25 Oct 2018

#### Fixed

* Fix with using beacons

## \[5.1.2] - 8 Oct 2018

#### Fixed

* Triggered trip timeout, persisting started triggered trip

## \[5.1.1] - 26 Sep 2018

#### Fixed

* SDK motion activity and start moving timing bug fixes

## \[5.1.0] - 27 Aug 2018

#### Added

* Meta Users implemented. Documentation updated accordingly.

## \[5.0.7] - 9 Aug 2018

#### Fixed

* Battery usage fix
