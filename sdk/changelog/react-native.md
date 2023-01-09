# React Native

## \[6.2.0] - 9 Jan 2023

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* Transport waypoint and distance information to `TransportEvent`, which is part of the event list returned in `UserContext`. Both waypoints and distance are based on unprocessed (i.e. raw) location data.
* Venue information inside StationaryEvent, which is part of the events list returned in `UserContext`.
* Venue significance and venue type information inside the `Venue` type.
* Semantic time information inside to `UserContext` type.

#### Changed

* BREAKING: _`startTimeEpoch`_ and _`endTimeEpoch`_ properties of objects returned part of the `UserContext` are now of type 'numeric', instead of 'string', and represent the Unix epoch time in milliseconds.
* BREAKING: _`longitude`_, _`latitude`_ and _`accuracy`_ properties of an `EventLocation` object returned part of the `UserContext` are now of type 'numeric', instead of 'string'.
* BREAKING: _the_ `EventLocation` type of the `UserContext` has been renamed into `GeoLocation`.
* Corrected the misspelled `BICYCLE` TransportMode type in the user context type definition file.
* Updated the Sentiance Android SDK dependency to version 6.2.
* Updated the Sentiance iOS SDK dependency to version 6.2.
* Updated the `isBatterySavingEnabled` and `isActivityRecognitionPermGranted` fields of the `SdkStatus` to cover iOS as well. (previously Android only)

#### Removed

* BREAKING: the `venueSignificance` and `venueCandidates` properties from the `UserContext` type have been removed. `VenueCandidate` and `Visit` classes have also been removed.
* BREAKING: venue `name` and `labels` properties are removed from `Venue`.

## \[6.1.2] - 3 Nov 2022

#### Fixed

* Typescript definition for UserCreationOptions in the `core` package.
* `npm i` installing an older beta package instead of latest stable, when no version is specified.

## \[6.1.1] - 30 Sep 2022

{% hint style="warning" %}
This version includes breaking changes for some [Early Access](../appendix/feature-production-readiness.md) features.
{% endhint %}

#### Added

* Diagnostic API for monitoring vehicle crash detection. See [here](../api-reference/react-native/crash-detection/#vehicle-crash-diagnostic-data).
* App-configurable rules to control SDK data transmission to the Sentiance Cloud Platform. The app can specify which of the following data types are allowed to be transmitted to the Sentiance platform: vehicle crash data, SDK and device info, general detection data, all data. See [here](../api-reference/react-native/core/#control-transmittable-data-types).
* Support for car, bus, train, and tram/metro transport mode detection, part of the user's current context information.

#### Changed

* Updated the Sentiance Android SDK dependency to version 6.1.
* Updated the Sentiance iOS SDK dependency to version 6.1.

#### Removed

* BREAKING: _vehicle_ and _rail_ transport modes from the user's current context information

## \[6.0.3] - 30 Aug 2022

#### Fixed

* The module names in the type definition files.
* Starting and stopping a trip on iOS via the core package.

## \[6.0.2] - 16 Aug 2022

#### Changed

* Relax the target Sentiance SDK versions, to include patches.

## \[6.0.1] - 1 Aug 2022

{% hint style="info" %}
**Breaking Changes**

Version 6.0 is a major release and includes multiple deprecations and breaking changes. Please read our [migration guide](../appendix/migration-guide/react-native.md) to learn how to update to this version.

Given the significance of the changes in this version, we recommend testing your app carefully, before making it available to your wider audience.
{% endhint %}

#### Added

* A function to check if a user exists on the device or not.
* Detection enabling and disabling functions that are persistent across app restarts, and that replace the SDK's start and stop functions.
* `userExists` and `isUserLinked` functions that are accessible without having to initialize the SDK.
* `setAppSessionDataCollectionEnabled(enabled)`
* `isAppSessionDataCollectionEnabled()`
* A Sentiance user creation function that supports the existing user-linking flow, and a new authentication-code based flow. The new flow is the recommended approach for future integrations.
* A `linkUser` function that supports linking a user following the existing user-linking flow.
* A `linkUserWithAuthCode` function that supports linking a user following the new authentication-code flow.
* An `addSdkStatusUpdateListener` function that supports registering listeners to get notified of SDK status updates without having to manually register a listener to the corresponding native device event.
* An `addTripTimeoutListener` function that supports registering listeners to get notified of SDK trip timeouts without having to manually register a listener to the corresponding native device event.
* An `addSdkUserActivityUpdateListener` function that supports registering listeners to get notified of SDK user activity updates without having to manually register a listener to the corresponding native device event.
* An `addVehicleCrashEventListener` function that supports registering listeners to get notified of SDK vehicle crash events without having to manually register a listener to the corresponding native device event.
* User Context information, which can be requested or subscribed for, and which includes a user's recent timeline events, the home and work locations (if detected), and a user's segments (if detected). This feature is released as [Early Access](../appendix/feature-production-readiness.md) and must be enabled by Sentiance first. For more information about it, see our [On-Device Features page](../appendix/on-device-features.md).

#### Changed

* Renamed `getUserAccessToken` to `requestUserAccessToken`
* Changed the return type of the `reset` function from `boolean` to `ResetResult`
* Changed the return type of `addUserMetadataField`, `addUserMetadataFields`, `removeUserMetadataField`, `disableBatteryOptimization` , `listenUserActivityUpdates` , `startTrip`, `stopTrip`, `submitDetections`, `updateSdkNotification` from `Promise<boolean>` to `Promise<void>`.
* Moved the `listenVehicleCrashEvents`, `invokeDummyVehicleCrash`, `isVehicleCrashDetectionSupported` functions to a separate `crash-detection` module.
* Bumped the target Android Sentiance SDK version to 6.0
* Bumped the target iOS Sentiance SDK version to 6.0

#### Deprecated

* `init(appId, secret, baseURL, shouldStart)`
* `initWithUserLinkingEnabled(appId, secret, baseURL, shouldStart)`
* `start()`
* `startWithStopDate(stopEpochTimeMs)`
* `stop()`
* `isNativeInitializationEnabled()`
* `enableNativeInitialization()`
* `disableNativeInitialization()`
* `isThirdPartyLinked()`
* `getValueForKey(key, defaultValue)`
* `setValueForKey(key, value)`
* `userLinkCallback(success)`
* `listenUserActivityUpdates()`
* `listenTripTimeout()`
