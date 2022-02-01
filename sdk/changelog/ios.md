# iOS

{% hint style="danger" %}
**Using Xcode 11 requires Sentiance SDK v5.5.2 and above**

Using Xcode 11 and targeting iOS SDK 13 breaks user linking on the Sentiance SDK. We have patched this in version **5.5.2** of our SDK. **Please make sure your app is up to date.**
{% endhint %}

{% hint style="danger" %}
&#x20;**Sentiance iOS SDK does not support arm64 simulator**

Due to the latest changes on Xcode 12.3, the Sentiance iOS SDK is not able to provide support for arm64 simulator.&#x20;

We recommend users continue their development using either an iOS device or an x86\_64 simulator while we're working on fixing things as fast as we can.
{% endhint %}

## \[5.12.0] - 4 January 2022

#### Fixed

* Trip recording consistency upon unexpected app restart.
* Stability of background task usage in the SDK.
* Improved vehicle crash detection.

**Deprecated**

* Legacy on-device trip profiling. This feature will be removed in the next major release.

## \[5.11.2] - 8 November 2021

#### Fixed

* Fixed updating debug log configuration received from backstage.
* Removed obsolete linker flag '-all\_load' from podspec which lead to linker issues in recent react native environments.

## \[5.11.1] - 29 July 2021

#### Fixed

* Fixed an issue where detections were not able to start on iOS 15 devices due to the updated authorization status.
* Fixed TensorFLowLite model updating mechanism at runtime.
* Removed embedded TensorFlowLite library from SENTSDK pod by providing a separate thinned package and adding a pod dependency to TensorFlowLite (applies to CocoaPods integration only and requires CocoaPods 1.10.0 **** or above).

## \[5.11.0] - 16 July 2021

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
* An improved and more accurate vehicle crash detection, backed by a machine learning model. You must switch to using the new Sentiance API method [`setVehicleCrashHandler:`](../api-reference/ios/sentsdk/#setvehiclecrashhandler) to activate it.
* A new method to help test your crash detection integration. See [`invokeDummyVehicleCrash`](../api-reference/ios/sentsdk/#invokedummyvehiclecrashhandler).
* A new method to check if crash detection is supported on the device for a specific trip type. See [`isVehicleCrashDetectionSupported:`](../api-reference/ios/sentsdk/#isvehiclecrashdetectionsupported).

{% hint style="warning" %}
**Beta Feature:** Support for host apps that enable[ Data Protection](https://developer.apple.com/documentation/uikit/protecting\_the\_user\_s\_privacy/encrypting\_your\_app\_s\_files). This functionality is released as a beta feature and not yet recommended for production use.
{% endhint %}

**Changed**

* The trip serialization process utilizes a less intense and more optimized background processing model.

**Deprecated**

* [`setCrashListener:`](../api-reference/ios/sentsdk/#setcrashlistener) is now deprecated. Use [`setVehicleCrashHandler:`](../api-reference/ios/sentsdk/#setvehiclecrashhandler)instead.

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
* [Integration Guide](../getting-started/ios-sdk/2.-configuration/integration-guide.md), to assist with installation and configuration of the SDK from Xcode

**Fixed**

* An issue that caused location observation to not stop properly when [`startWithStopDate:completion:`](https://docs.sentiance.com/sdk/api-reference/ios/sentsdk#startwithstopdate) is used

## \[5.4.0] - 2 July 2019

#### Added

* Method to [set stop date on SDK](../api-reference/ios/sentsdk/#startwithstopdate)
* new SENTStartStatus: [SENTStartStatusExpired](../api-reference/ios/sentsdk/sentsdkstatus.md#startstatus)

## \[5.3.2] - 14 Jun 2019

#### Added

* Method to set[ vehicle crash listener.](https://docs.sentiance.com/sdk/appendix/detecting-vehicle-crashes)

## \[5.3.0] - 4 Jun 2019

#### Added

* Method to set [user activity listener](../api-reference/ios/sentsdk/#setuseractivitylisterner).
* Method to get [current user activity](../api-reference/ios/sentsdk/#getuseractivity).

## \[5.2.1] - 29 May 2019

#### Added

* Method to [add metadata during](../api-reference/ios/sentsdk/#addtripmetadata) the trip.
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
