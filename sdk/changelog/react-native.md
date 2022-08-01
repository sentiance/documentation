# React Native

## \[6.0.1] - 1 Aug 2022

{% hint style="info" %}
**Breaking Changes**

Version 6.0.0 is a major release and includes multiple deprecations and breaking changes. Please read our [migration guide](../appendix/migration-guide/react-native.md) to learn how to update to this version.

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