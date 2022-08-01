# iOS

## Migrating from 5.x to 6.x

Version 6.x brings a lot of improvements and new features to the Sentiance SDK, like a simpler API for initialization, user creation, authentication and linking users. Some of these improvements result in breaking changes in the existing integration. This section describes all the changes that were made since version 5.15.0, and provides two code migration paths: a minimal one that utilizes existing (but deprecated) APIs, and a full one that utilizes only the new APIs.

{% hint style="info" %}
Please note that new SDK features and functionality will be supported via new API methods and classes. As such, you are encouraged to do a full migration, in order to benefit from upcoming features and improvements.
{% endhint %}

### **General Changes**

#### Minimum Supported iOS Version

We have bumped the minimum supported iOS version to 13.0. You can still target iOS 12.0 in your app, but the SDK will initialize and operate only on iOS 13.0 and above.

#### Fat .framework Artifact

We will no longer provide our SDK as a fat **.framework**. We will instead offer two variants of **.xcframework** artifacts:

* A thin one which is referenced by our podspec and used for CocoaPods integrations.
* A regular one which bundles other dependency frameworks as mentioned below.&#x20;

#### Dependencies

Apart from TensorFlow Lite v2.7, the SDK now has the following additional dependencies.

* Protobuf: v3.18
* UnzipKit: v1.9

These dependencies are bundled as xcframeworks within our regular xcframework, which you can utilize when doing a manual integration. If you are using CocoaPods (which references our thin framework), we have updated the SDK _podspec_ to include these dependencies.

#### SDK Bundle

The bundle that is included in the SENTSDK framework has been updated. If you've done a manual integration, please make sure that you update **SENTSDK.bundle** in your project**.**

#### Background Modes

We have added background task scheduling capabilities in the SDK, to run maintenance and feature related operations in the background. This requires _Background fetch_ and _Background processing_ capabilities to be enabled for your app (Project settings -> select a target -> Signing & Capabilities -> Background Modes).

Additionally, the following task identifiers must be added to the project info (Info.plist), if you'd like to utilize the SDK's [on-device features](../on-device-features.md).

* com.sentiance.backgroundtask.tilerefresh
* com.sentiance.backgroundtask.segment\_detection

You can add these by following these steps:

1. Project settings -> select a target -> Info.
2. Add "Permitted background task scheduler identifiers".
3. Add the above identifiers as sub-items.

### Code Changes & Deprecations

We have updated the SDK API methods and classes to make it easier to integrate our SDK into your app and to conform more to Swift standards. While doing so, we have renamed and removed some classes, methods, and properties, and deprecated others. Deprecated APIs will still function properly, however we plan to remove them in the next major release.

#### Nullability Specification

We have applied proper nullability annotations to all our public API classes and methods.

#### Shared Instance

In Swift, `SENTSDK.sharedInstance()` has been replaced with the more concise `Sentiance.shared` _****_ for accessing the Singleton instance of the SDK.

#### Invoking SDK Methods

SDK methods can no longer be invoked without first having initialized the SDK, unless it is stated otherwise in the method's documentation. For example, you must not call `submitDetections` without having initialized the SDK, but you are allowed to call `userExists` to check whether a Sentiance user us present. Check each method's documentation to know more.

#### Callback Execution Thread

Unless otherwise documented, callback or handler methods that are passed to the SDK are executed on the main thread. Be sure to check that you're not running intensive operations within these methods.

#### **Renamed Classes and Methods**

The following classes and methods have been renamed:

|         Old Name        |         New Name        |
| :---------------------: | :---------------------: |
|      MetaUserLinker     |      SENTUserLinker     |
| setTripTimeOutListener: | setTripTimeoutListener: |

#### &#x20;**Swift Friendly Properties**

The following deprecated methods now have alternative Swift friendly properties:

|      Old Method     |   New Property   |
| :-----------------: | :--------------: |
|     getInitState    |     initState    |
|     getSDKStatus    |     sdkStatus    |
|      getVersion     |      version     |
|  getWifiQuotaLimit  |  wifiQuotaLimit  |
|  getWifiQuotaUsage  |  wifiQuotaUsage  |
| getMobileQuotaLimit | mobileQuotaLimit |
| getMobileQuotaUsage | mobileQuotaUsage |
|  getDiskQuotaLimit  |  diskQuotaLimit  |
|  getDiskQuotaUsage  |  diskQuotaUsage  |

#### **Renamed Enums**

The `SENTSDKInitState` enum values have been updated for easier usage in Swift code.

|      Old Name      |            New Name            |
| :----------------: | :----------------------------: |
| SENTInitInProgress |   SENTSDKInitStateInProgress   |
|   SENTInitialized  |   SENTSDKInitStateInitialized  |
|    SENTResetting   |    SENTSDKInitStateResetting   |
| SENTNotInitialized | SENTSDKInitStateNotInitialized |

#### SDK Status

The `isLocationPermGranted` property has been deprecated and replaced with the new enum property `locationPermission`.

The `startStatus` **** property has been deprecated and replaced with `detectionStatus`_**.**_

#### Asynchronous Methods

Existing asynchronous SDK methods have been deprecated. New asynchronous methods have been added with a `completionHandler` with `Result` and `Error` **** as returned parameter types.

```swift
Sentiance.shared.submitDetections { result, error in
    guard let result = result else {
        // Error 
    }
    
    // Handle successful result
}
```

#### SDK Initialization & User Creation

The existing SDK initializer served two purposes:

1. Create a Sentiance user if one does not exist;
2. Initialize internal SDK components and resume detections.

We have deprecated the existing initializer `initWithConfig` in favour of a new method called `initializeWithOptions`. This new method **does not create a Sentiance user**. Instead, if a Sentiance user already exists, it initializes the SDK internally and resumes detections (if detections were enabled in the past).

To create a Sentiance user, we have added a new method called `createUser`. You can use this method to create a Sentiance user anywhere in your app. Note that you can only create one user at any time. To create a different user, you must first reset the SDK.

Given that user creation is not part of initialization anymore, **we expect apps to initialize the SDK during app startup, without postponing or delaying it**. The new initializer can safely be called when a Sentiance user does not exist yet, as it will only do minimal work to prepare the SDK for user creation.

{% hint style="warning" %}
As long as a Sentiance user exists on the device, you are expected to initialize the SDK during app startup, without delay or postponement. If you intend to not run detections for a brief period, simply call _disableDetections_ instead. **** If you intend to not run detections for a longer duration, simply reset the SDK to remove the user from the device.
{% endhint %}

The deprecated method `isInitialized()` from `Sentiance` has also been removed. Use `initState` property instead.

#### Checking User Existence & Linking Status

You can use the new `userExists` property to find out whether a Sentiance user already exists. And to check whether the user has been successfully linked (i.e. user linking), you can use `isUserLinked`.

Unlike the other SDK methods, these two methods can be called without needing to initialize the SDK first.

### **Minimal Migration Steps**

The following steps describe the minimal changes that you have to do, in order to compile and run your app with v6.x of the Sentiance SDK. Depending on your development environment and integration method, you might need to make additional changes that are not mentioned here. If you haven't already done so, please go through the [General Changes](ios.md#general-changes) section in order to get a complete list of the changes that were made in version 6.x.

#### **1. Update the SDK Dependency**

Your dependency manager should point to version 6.0.0 of the Sentiance SDK.

#### 2. Enable Background Modes

Enable the additional background modes in your project's capabilities setting page. See [here](ios.md#background-modes).

#### **3. Apply Code Changes**

* Replace the usage of `SENTSDK.sharedInstance()` with `Sentiance.shared`
* Replace the usage of `MetaUserLinker` class with `SENTUserLinker`
* Rename the enum values for `SENTSDKInitState` as described [here](ios.md#undefined).
* Replace the usage of the `SENTSDKStatus.isLocationPermGranted` property with `SENTSDKStatus.locationPermission`.
* Adapt to the nullability changes that impact the optional/non-optional nature of arguments.
* The existing initializer method `initWithConfig` copies the properties from the `SENTConfig` during initialization. If you currently update the `SENTConfig` after passing it to the initializer, the update will not be consumed. Move your code to before invoking the initializer.
* Remove the argument from `isVehicleCrashDetectionSupported`

### Full Migration Steps

The following steps describe all the change that you have to do, in order to replace deprecated Sentiance API usage with non-deprecated counterparts, and successfully compile and run your app after updating to v6.x. Depending on your development environment and integration method, you might need to make additional changes that are not mentioned here. If you haven't already done so, please go through the [General Changes](ios.md#general-changes) section in order to get a complete list of the changes that were made in version 6.x.

#### **1. Update the SDK Dependency**

Your dependency manager should point to version 6.0.0 of the Sentiance SDK.

#### 2. Enable Background Modes

Enable the additional background modes in your project's capabilities setting page. See [here](ios.md#background-modes).

#### **3. Update the SDK Initialization**

In your existing integration, you initialize the Sentiance SDK by calling `initWithConfig` from within your Application's `didFinishLaunchingWithOptions` method. Replace `initWithConfig` with the new `initializeWithOptions` method. This method accepts a `SENTOptions` object.

The following options are no longer available as initialization options:

* User linker; you need to pass a linker when creating a user instead.
* Sentiance credentials (i.e. app ID & secret); you will only need to specify these once, when creating a Sentiance user.
* SDK status update handler; use the `setDidReceiveSdkStatusUpdateHandler:` method from to listen to status updates.
* [Triggered trips flavor](../controlled-detections/controlled-trips-only.md): it's not possible to set this flavor programmatically anymore. This must be configured for your app on the Sentiance platform. Please reach out to our support team to make sure it is configured properly.

Moreover, the new `SENTOptions` class requires specifying the purpose of its use. When creating an instance that will be used for initializing the SDK in the app delegate (during app launch), set it to `SENTOptionsInitPurposeAppLaunch`. This will allow the SDK initializer to execution certain actions that should only be done from within the app delegate, for example, registering background task identifiers.

If you specify a `baseURL` in the `SENTConfig` that you pass to the existing initializer, you should set the URL to the `platformUrl` property of the `SENTOptions` object that you will pass to the `initializeWithOptions` method.

{% hint style="info" %}
For a completely new integration, where you're not migrating an existing user, you do not need to specify the platform URL during initialization. Instead, you specify it during user creation.
{% endhint %}

The Sentiance SDK must be initialized before creating a user. Therefore, remove any conditional checks that require the presence of a user before initializing the SDK. Calling `initializeWithOptions` during app startup when there is no Sentiance user yet will not create a user. It will only do the necessary setup to make it possible to create a user later on.

Initialization is now always synchronous, and therefore you will receive the result as an `SENTInitializationResult` object after calling `initializeWithOptions`.

{% hint style="info" %}
#### Detecting Incorrect Initializations

We expect apps to initialize the Sentiance SDK during app startup, without any postponement. Therefore, the new initializer must be called synchronously on the main thread, before `didFinishLaunchingWithOptions` __ completes ([more about this requirement](../sdk-initialization.md)).

To assist you with the integration, we have added a mechanism for detecting most common incorrect initializations. When detected, the SDK will log a warning message in the console, with a link to our documentation.
{% endhint %}

#### 4. Enable Detections

Having replaced the deprecated SDK initializer with the new one, you need to make a follow up change by replacing the SDK's start invocation with `enableDetections`. As the start call was being done after a successful initialization, you need to call `enableDetections` after the new initializer succeeds. Your code should therefore look as follows:

```swift
let result = Sentiance.shared.initialize(options: options)
if (result.isSuccessful) {
    Sentiance.shared.enableDetections { result, error in   
    }
}
```

Note that enabling detections (i.e. starting the SDK) is now persistent. Therefore, calling `enableDetections` is not necessary upon every app startup, but doing so does not have any side effects. For purposes of this migration, you'll have to enable detections at least one time after initializing the SDK. In a complete new integration, the call to `enableDetections` can normally be placed elsewhere in the application's flow, usually after user creation.

#### **5. Update User Creation**

In your existing integration, you will likely have some conditional logic inside `initWithConfig` to create a Sentiance user. Replace this call with `createUser`. This method accepts `UserCreationOptions`, allowing you to specify the Sentiance app credentials (app ID and secret), the Sentiance platform URL (optional), and a user linker. If your existing integration does not make use of user linking, pass `nil` as the linker.

{% hint style="info" %}
**User Creation Without the Need for App Credentials**

In addition to the user-linker based approach of creating users, we have introduced an improved linked-user creation mechanism, which replaces the Sentiance app credentials with a temporary authentication code, obtained from Sentiance at the moment of user creation. This is our recommended approach for creating users in all new integrations. You can read more about it [here](../user-creation.md).
{% endhint %}

`createUser` has a completion handler with result and error as arguments, which you can use to capture the user creation result or the corresponding error in case of failure.

#### 6. Update Enabling/Disabling Detections

We have deprecated the existing `start()` and `stop()` methods, and replaced them with `enableDetections()` and `disableDetections()` respectively. We believe these new methods give more clarity on what `start` and `stop` did in the past, as calling `start` did not always start detections, for example, due to a detection issue (e.g. in case of insufficient permissions).

These new methods are **persistent across app restarts and device reboots**. Therefore, you normally only need to call them once (e.g. after user creation), and the SDK will automatically resume (or halt) detections upon initialization.

We've also added a new property called `detectionStatus` which we believe offers better clarity on the status of the detections. The possible results are: `SENTDetectionStatusDisabled`, `SENTDetectionStatusExpired`, `SENTDetectionStatusEnabledButBlocked`, and `SENTDetectionStatusEnabledAndDetecting`. For cases when the detections are blocked, the `SENTSDKStatus` is still available to get more information about what is blocking detections (e.g. insufficient permissions).

#### 7. Switch to Using Properties

For the deprecated methods that have been replaced with properties, switch to using the properties. See [here](ios.md#swift-friendly-properties).

#### 8. Update Other Asynchronous Method Usages

Replace the usage of the following asynchronous SDK methods with their new counterparts with a result and error based completion handler:

| Deprecated Method                             | Replacement Method                                                        |
| --------------------------------------------- | ------------------------------------------------------------------------- |
| start:completion:                             | enableDetectionsWithCompletionHandler:                                    |
| startWithStopDate:completion:                 | enableDetectionsWithExpiryDate: completionHandler:                        |
| stop                                          | disableDetectionsWithCompletionHandler:                                   |
| getUserAccessToken:failure:                   | requestUserAccessTokenWithCompletionHandler:                              |
| startTrip:transportModeHint: success:failure: | <p>startTripWithMetadata:<br>transportModeHint:<br>completionHandler:</p> |
| stopTrip:failure:                             | stopTripWithCompletionHandler:                                            |
| submitDetections:failure:                     | submitDetectionsWithCompletionHandler:                                    |
| requestUserContext:failure:                   | requestUserContextWithCompletionHandler:                                  |
| reset:failure:                                | resetWithCompletionHandler:                                               |

#### 9. Update Other Code Usages

* Replace the usage of `SENTSDK.sharedInstance()` with `Sentiance.shared`
* Rename the enum values for `SENTSDKInitState` as described [here](ios.md#undefined).
* Replace the usage of the `SENTSDKStatus.isLocationPermGranted` property with `SENTSDKStatus.locationPermission`.
* Adapt to the nullability changes that impact the optional/non-optional nature of arguments.
* Remove the argument from `isVehicleCrashDetectionSupported`

## Migrating from 4.6.x to 5.x

### Updating compiler build settings

1\. Go to the **Build Settings** tab of your target settings \
2\. Look for **Other Linker Flags** in the **Linking** section. \
3\. Add `-lc++` flag

### Include the SDK bundle in your project

1\. Go to the **Build Phases** tab of your target settings \
2\. Expand the **Copy Bundle Resources** row and click the `+` button \
3\. Choose the `SENTSDK.bundle` file located inside `SENTSDK.framework`

### Permission message

Make sure a value for the key `NSLocationAlwaysAndWhenInUseUsageDescription`has been added to the **Info.plist**

### Sentiance SDK import update

Replace `#import <SENTTransportDetectionSDK/SENTTransportDetectionSDK.h>` to `@import SENTSDK;` in the import section

### CoreData import

Make sure you have added `CoreData` library as linked framework in your Xcode project

### User access token API change

If you need to get the user access token, use the code below

```objectivec
Sentiance.shared.requestUserAccessToken { result, error in
    guard let result = result else {
        // error
        print("Error: \(error!.failureReason)")
        return
    }
        
    print("Token: \(result.token)")
}
```

### SDK Control

The `stopAfter(seconds)` method is no longer available.

### User Metadata

User metadata methods no longer accept a `success/failure` block parameter. Adding and removing metadata is now done asynchronously via the payload submission system.

### External Events

Registering external events is no longer available.

### Trip Control

#### Starting and Stopping Trips

`startTrip()` and `stopTrip()` methods now require a `success` and `failure(sdkStatus)` block parameters respectively.

#### Trip Details

The SDK no longer returns a `Trip` object when a trip is stopped. The `setTripTimeOutListener()` callback of the SDK no longer returns a `Trip` object.

#### Checking Ongoing Trips

The `isTripOngoing()` method now expects a parameter of type `TripType`.

### Other

`getWiFiLastSeenTimestamp()` is no longer available.
