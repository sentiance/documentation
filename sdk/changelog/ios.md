# iOS

## \[5.6.0\] - 5 Feb 2020

**Added**

* Support for [reset](https://docs.sentiance.com/sdk/api-reference/ios/sentsdk#reset)ting the SDK to factory settings, which clears all user data and allows creating a new Sentiance user

**Fixed**

* An issue where the SDK database might experience conflicts when the enclosing app also uses database instance\(s\) of CoreData

**Changed**

* The geo-fence management policy so that the SDK does not intervene with the lifecycle of geo-fences owned by the enclosing app

## \[5.5.5\] - 13 Nov 2019

* Fixed the SDK start/stop infinite loop when the user was selecting “Allow Once” for iOS 13 location permission

## \[5.5.3\] - 7 Oct 2019

**Fixed**

* _iOS 13_ background tasks crash
* Stuck in stationary \(missing some trips\)
* On base url change submission fix

## \[5.5.2\] - 17 Sept 2019

#### Fixed

* _iOS 13_ crash fix
* Payload submission stability fixes

## \[5.5.1\] - 27 Aug 2019

#### Added

* Support for [CocoaPods](https://cocoapods.org)
* [Integration Guide](../getting-started/ios-sdk/2.-configuration/integration-guide.md), to assist with installation and configuration of the SDK from Xcode

**Fixed**

* An issue that caused location observation to not stop properly when [`startWithStopDate:completion:`](https://docs.sentiance.com/sdk/api-reference/ios/sentsdk#startwithstopdate) is used

## \[5.4.0\] - 2 July 2019

#### Added

* Method to [set stop date on SDK](../api-reference/ios/sentsdk/#startwithstopdate)
* new SENTStartStatus: [SENTStartStatusExpired](../api-reference/ios/sentsdk/sentsdkstatus.md#startstatus)

## \[5.3.2\] - 14 Jun 2019

#### Added

* Method to set[ vehicle crash listener.](https://docs.sentiance.com/sdk/appendix/detecting-vehicle-crashes)

## \[5.3.0\] - 4 Jun 2019

#### Added

* Method to set [user activity listener](../api-reference/ios/sentsdk/#setuseractivitylisterner).
* Method to get [current user activity](../api-reference/ios/sentsdk/#getuseractivity).

## \[5.2.1\] - 29 May 2019

#### Added

* Method to [add metadata during](../api-reference/ios/sentsdk/#addtripmetadata) the trip.
* Method to [set base API](../api-reference/ios/sentconfig-1.md#baseurl) url for SDK.

#### Changed

* Stability and trip detection improvements.

#### Fixed

* Fix with reachability.

## \[5.1.8\] - 28 Feb 2019

#### Changed

* Stability improvements.

## \[5.1.7\] - 28 Jan 2019

#### Added

* Crash detection speed check.

#### Changed

* Improved trip start detection.
* Stability improvements.

## \[5.1.5\] - 21 Dec 2018

#### Fixed

* iOS update fix
* Trip overlays on off the grid events
* Other fixes and improvements

## \[5.1.4\] - 6 Nov 2018

#### Added

* Crash detection implemented

#### Fixed

* Fix with small amount of waypoints
* Trip duplication fix
* Other fixes and improvements

## \[5.1.3\] - 25 Oct 2018

#### Fixed

* Fix with using beacons

## \[5.1.2\] - 8 Oct 2018

#### Fixed

* Triggered trip timeout, persisting started triggered trip

## \[5.1.1\] - 26 Sep 2018

#### Fixed

* SDK motion activity and start moving timing bug fixes

## \[5.1.0\] - 27 Aug 2018

#### Added

* Meta Users implemented. Documentation updated accordingly.

## \[5.0.7\] - 9 Aug 2018

#### Fixed

* Battery usage fix

