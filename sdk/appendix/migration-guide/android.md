# Android

## Migrating from 4.x to 6.x

Version 6.x brings a lot of improvements and new features to the Sentiance SDK, like a simpler API for initialization, user creation, authentication and linking users. Some of these improvements result in breaking changes in the existing integration. This section describes all the changes that were made since version 4.22.1, and provides two code migration paths: a minimal one that utilizes existing (but deprecated) APIs, and a full one that utilizes only the new APIs.

{% hint style="info" %}
Please note that new SDK features and functionality will be supported via the new API methods and classes. As such, you are encouraged to do a full migration, in order to benefit from upcoming features and improvements.
{% endhint %}

### General Changes

#### Minimum Supported Android Version

We have bumped the minimum supported Android version to 6.0 (Marshmallow—API level 23). If you target an older version of Android, please see [this](../../troubleshooting/android/#manifest-merger-failed-uses-sdk-minsdkversion-x-cannot-be-smaller-than-version-y-declared-in-library) troubleshooting guide to learn how to resolve related issues.

#### Java 8 Compatibility

Version 6.x makes use of Java 8 language features. Make sure your app is configured to support Java 8. See [this](https://developer.android.com/studio/write/java8-support#supported\_features) guide.

#### Proguard Rules

Version 4.x automatically applied the following rule when compiling your app:

```
-keepattributes SourceFile, LineNumberTable
```

Though beneficial for [troubleshooting crashes](https://developer.android.com/studio/build/shrink-code?authuser=0\&hl=sr-CS\&skip\_cache=true#decode-stack-trace) using stack traces, there was no way for developers to omit this rule if desired to do so. In version 6.x, we have omitted this rule from our libraries.

{% hint style="warning" %}
**Important**

If you want to retain debugging information for your app (e.g. to troubleshoot crashes), make sure that this rule exists in your app's own proguard rules file.
{% endhint %}

#### Google Play Services Location Library

We have updated the minimum required version of the Google Play Services location library (com.google.android.gms:play-services-location) to 18.0.0. If your app targets a different version, please note that Gradle will automatically pick the highest one. You can verify which version is being picked by running:

```
$ ./gradlew app:dependencies

...
releaseRuntimeClasspath - Runtime classpath of compilation 'release' (target  (androidJvm)).
+--- com.sentiance:sdk:6.0.0
|    +--- com.google.android.gms:play-services-location:18.0.0
```

You should see something similar to line 6 above. However, if you have explicitly excluded the location library from the Sentiance SDK's transitive dependencies (see the below example), please either omit this exclusion, or update the location library version defined in your app's dependencies.

{% code title="build.gradle" %}
```groovy
// If you have an exclusion rule similar to line 7, either omit it or 
// update your own GMS location library version (line 10).

dependencies {
	implementation ('com.sentiance:sdk:4.19.2@aar') {
		transitive = true
		exclude group: 'com.google.android.gms'
	}
	
	implementation "com.google.android.gms:play-services-location:18.0.0"
}
```
{% endcode %}

After making the above change, run `./gradlew app:dependencies` to verify the chosen library version.

#### Android Support Libraries

As version 4.x targeted an older version of the Google Play Service location library, it brought along with it some old android-support transitive dependencies. With the version 18.0.0, these support libraries have now been replaced with their AndroidX counterparts.

#### SDK Artifacts & Dependencies

Version 6.x breaks down SDK features and functionality into multiple artifacts, each with its own dependencies. Check [this page](../android/artifacts-dependencies.md) to see all the artifacts and dependencies.

{% hint style="warning" %}
If you reference our SDK as a local aar file inside your project, or by hosting it in a private repository, please make sure all of the new dependencies are met, including transitive ones.&#x20;
{% endhint %}

The core Sentiance functionality is provided by the _com.sentiance:sdk_ artifact. This includes operations like creating a Sentiance user, and starting detections. Other library artifacts act as extensions that include additional Sentiance features and functionality. For example, _com.sentiance:sdk-crash-detection_ includes the crash detection feature.

To enable these additional features, you need to add the corresponding artifact as a dependency in your app. You can make use of the SDK's bill of materials (BOM) artifact to reference a single version and avoid incompatibility issues:

{% code title="build.gradle" %}
```groovy
dependencies {
    ...
    implementation(platform('com.sentiance:sdk-bom:6.0.0'))
    implementation('com.sentiance:sdk')
    implementation('com.sentiance:sdk-crash-detection')
}
```
{% endcode %}

{% hint style="warning" %}
Some features must be activated by Sentiance before you can start using them. Please reach out to our support team to make sure that the feature you want to use is activated.
{% endhint %}

#### Android XML Backup Rules

The [XML Android backup rules](https://developer.android.com/guide/topics/data/autobackup#IncludingFiles) that are applied by the Sentiance SDK have been updated. If you have overwritten the backup rules in your app's manifest, please update it by including any missing SDK rule. See [this](../../troubleshooting/android/#manifest-merger-failed-attribute-fullbackupcontent) troubleshooting guide.

### Code Changes & Deprecations

We have updated the SDK API methods and classes to make it easier to integrate our SDK into your app. By doing so, we have deprecated some existing API methods and classes. These APIs will still function properly, however we plan to remove them in the next major release.

#### User Linking

The following classes and interfaces under the _com.sentiance.sdk_ package have been renamed:

|        Old Name        |      New Name      |
| :--------------------: | :----------------: |
|     MetaUserLinker     |     UserLinker     |
|   MetaUserLinkerAsync  |   UserLinkerAsync  |
| MetaUserLinkerCallback | UserLinkerCallback |

The `setMetaUserLinker` method of the `SdkConfig.Builder` class has been renamed to `setUserLinker`.

#### SdkStatus

The `startStatus` field has been deprecated. The new `detectionStatus` field has been added as its successor.

The boolean status field `isLocationPermGranted` has been removed, and replaced with a new enum field [**locationPermission**](../../api-reference/android/sdkstatus/#locationpermission).

#### Crash Detection

Crash detection is now made available via a separate library artifact. You therefore need to add _com.sentiance:sdk-crash-detection_ as a dependency to your app, in order to activate the feature.

The new entry point for crash detection related functionality is the `CrashDetectionApi` class. The following methods have therefore been removed from the `Sentiance` class and are now available in the `CrashDetectionApi` class:

* `invokeDummyVehicleCrash` (no signature change)
* `setVehicleCrashListener` (no signature change)
* `isVehicleCrashDetectionSupported` (signature update: the `TripType` parameter has been removed)

Additionally, the following classes and interfaces have been moved to the _com.sentiance.sdk.crashdetection.api_ package:

* `VehicleCrashEvent` (the existing properties of this class are no longer nullable).
* `VehicleCrashListener`

Lastly, the following (previously deprecated) API classes and methods have been removed:

* `com.sentiance.sdk.crashdetection.CrashCallback`
* `Sentiance.setCrashCallback(CrashCallback callback)`

#### Asynchronous Methods

Existing asynchronous SDK methods have been deprecated. New asynchronous methods have been added, that return a [`PendingOperation<Result, Error>`](../../api-reference/android/pendingoperation/), which is similar to the [Java Future](https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/Future.html).

`PendingOperation` allows you to set success, failure, and completion handlers to asynchronously handle an operation's result.

```kotlin
// Enable SDK detections and 
val pendingOperation = sentiance.enableDetections()
    .addOnSuccessListener { result ->
        //...
    }
    .addOnFailureListener { error -> 
        //...
    }
    .addOnCompleteListener { operation ->
        if (operation.isSuccessful) {
            //...
        } else {
            //...
        }
    }
```

Moreover, it offers the possibility to wait for the result up to a certain duration, or until completion.

```kotlin
// Wait 30 seconds
val pendingOperation = sentiance.enableDetections().waitFor(30, TimeUnit.SECONDS)

// Wait till completion
val pendingOperation = sentiance.enableDetections().waitTillCompletion()
```

To learn more about what `PendingOperation` offers, see the API reference page [here](../../api-reference/android/pendingoperation/).

#### SDK Initialization & User Creation

The existing SDK initializer served two purposes:

1. Create a Sentiance user if one does not exist;
2. initialize internal SDK components and resume detections.

We have deprecated the existing initializer `init` in favor of a new method called `initialize`. This new method **does not create a Sentiance user**. Instead, if a Sentiance user already exists, it initializes the SDK internally and resumes detections (if detections were enabled in the past).

To create a Sentiance user, we have added a new method called `createUser`. You can use this method to create a Sentiance user anywhere in your app. Note that you can only create one user at any time. To create a different user, you must first reset the SDK.

Given that user creation is not part of initialization anymore, **we expect apps to initialize the SDK during app startup, without postponing or delaying it**. The new initializer can safely be called when a Sentiance user does not exist yet, as it will only do minimal work to prepare the SDK for user creation.

{% hint style="warning" %}
As long as a Sentiance user exists on the device, you are expected to initialize the SDK during app startup, without delay or postponement. If you intend to not run detections for a brief period, simply call _disableDetections_ instead. **** If you intend to not run detections for a longer duration, simply reset the SDK to remove the user from the device.
{% endhint %}

The deprecated method `isInitialized()` from `Sentiance` has also been removed. Use `getInitState()` instead.

#### Checking User Existence & Linking Status

You can use the new `userExists()` method to find out whether a Sentiance user already exists. And to check whether the user has been successfully linked (i.e. user linking), you can call `isUserLinked()`.

Unlike the other SDK methods, these two methods can be called without needing to initialize the SDK first.

### **Minimal Migration Steps**&#x20;

The following steps describe the minimal changes that you have to do, in order to compile and run your app with v6.x of the Sentiance SDK. Depending on your development environment and integration method, you might need to make additional changes that are not mentioned here. If you haven't already done so, please go through the [General Changes](android.md#general-changes) section in order to get a complete list of the changes that were made in version 6.x.

#### 1. Add Java 8 Support

Make sure your app supports Java 8. See [this](https://developer.android.com/studio/write/java8-support#supported\_features) guide.

#### 2. Update the SDK Dependency

In your app, update the Sentiance SDK dependency to use the BOM artifact, and reference v6.x of the SDK. See [SDK Artifacts and Dependencies](android.md#sdk-artifacts-and-dependencies).

If your app makes use of the vehicle crash detection feature, add the _com.sentiance:sdk-crash-detection_ dependency.

#### 3. Update the Android XML Backup Rules

If you have specified custom backup rules in your app's manifest file, add the missing SDK rules. See [here](../../troubleshooting/android/#manifest-merger-failed-attribute-fullbackupcontent).

#### 4. Apply Code Changes

* For user linking, update the class and interface names. See [here](android.md#user-linking).
* Replace the SDK status `isLocationPermGranted` field usage with `locationPermission`.&#x20;
* Replace `isInitialized()` usage with `getInitState()`.
* For vehicle crash detection, update the package name of the imported classes and utilize the `CrashDetectionApi` class to access the crash detection methods with their updated signatures. See [here](android.md#crash-detection). If you were using the deprecated crash detection methods from the `Sentiance` class, migrate to the new ones.

### Full Migration Steps

The following steps describe all the changes that you have to do, in order to replace deprecated Sentiance API usage with non-deprecated counterparts, and successfully compile and run your app after updating to v6.x. Depending on your development environment and integration method, you might need to make additional changes that are not mentioned here. If you haven't already done so, please go through the [General Changes](android.md#general-changes) section in order to get a complete list of the changes that were made in version 6.x.

#### 1. Add Java 8 Support

Make sure your app supports Java 8. See [this](https://developer.android.com/studio/write/java8-support#supported\_features) guide.

#### 2. Update the SDK Dependency

In your app, update the Sentiance SDK dependency to use the BOM artifact, and reference v6.x of the SDK. See [SDK Artifacts and Dependencies](android.md#sdk-artifacts-and-dependencies).

If your app makes use of the vehicle crash detection feature, add the _com.sentiance:sdk-crash-detection_ dependency.

#### 3. Update the Android XML Backup Rules

If you have specified custom backup rules in your app's manifest file, add the missing SDK rules. See [here](../../troubleshooting/android/#manifest-merger-failed-attribute-fullbackupcontent).

#### 4. Update the SDK Initialization

In your existing integration, you initialize the Sentiance SDK by calling `init` from within your Application's `onCreate` method. Replace `init` with the new `initialize` method. This method accepts a `SentianceOptions` object which you can create using its `Builder`. You can set a custom Android notification that the SDK can use via this `Builder`.

The following options are no longer available as initialization options:

* Base URL (i.e. Sentiance platform URL): you will only need to specify this once, when creating a Sentiance user.
* User linker: you will need to pass a linker when creating a user instead.
* Sentiance credentials (i.e. app ID & secret): you will only need to specify these once, when creating a Sentiance user.
* SDK status update handler: use the `setSdkStatusUpdateListener` method from `Sentiance`.
* [Triggered trips flavor](../controlled-detections/controlled-trips-only.md): it's not possible to set this flavor programmatically anymore. This must be configured for your app on the Sentiance platform. Please reach out to our support team to make sure it is configured properly.

The Sentiance SDK must be initialized before creating a user. Therefore, remove any conditional checks that require the presence of a user before initializing the SDK. Calling `initialize` during app startup when there is no Sentiance user yet will not create a user. It will only do the necessary setup to make it possible to create a user later on.

Initialization is now always synchronous, and therefore you will receive the result as an `InitializationResult` object after calling `initialize`.

{% hint style="info" %}
#### Detecting Incorrect Initializations

We expect apps to initialize the Sentiance SDK during app startup, without any postponement. Therefore, the new initializer must be called synchronously on the main thread, before _Application.onCreate()_ **** completes ([more about this requirement](../sdk-initialization.md)).

To assist you with the integration, we have added a notification mechanism for detecting most common incorrect initializations. When detected, the SDK will show a notification with a warning message, and a link to our documentation (when tapped). This notification is limited to debug builds of your app, and can be disabled via _SentianceOptions_.
{% endhint %}

#### 5. Update the User Creation

In your existing integration, you will likely have some conditional logic that calls `init` to create a Sentiance user. Replace this call with `createUser`. This method accepts `UserCreationOptions`, allowing you to specify the Sentiance app credentials (app ID and secret), the Sentiance platform URL (optional), and a user linker. If your existing integration does not make use of user linking, pass `UserLinker.NO_OP` as the linker.

{% hint style="info" %}
**User Creation Without the Need for App Credentials**

In addition to the user-linker based approach of creating users, we have introduced an improved linked-user creation mechanism, which replaces the Sentiance app credentials with a temporary authentication code, obtained from Sentiance at the moment of user creation. This is our recommended approach for creating users in all new integrations. You can read more about it [here](../user-creation.md).
{% endhint %}

`createUser` returns the newly introduced `PendingOperation`, which you can use to capture the user creation result.

#### 6. Update Enabling/Disabling Detections

We have deprecated the existing `start()` and `stop()` methods, and replaced them with `enableDetections()` and `disableDetections()` respectively. We believe these new methods give more clarity on what `start` and `stop` did in the past, as calling `start` did not always start detections, for example, due to a detection issue (e.g. in case of insufficient permissions).

These new methods are **persistent across app restarts and device reboots**. Therefore, you only need to call them once, and the SDK will automatically resume (or halt) detections upon initialization.

Additionally, we've added a new method called `getDetectionStatus()` which we believe offers better clarity on the status of the detections. The possible results are: `DISABLED`, `EXPIRED`, `ENABLED_BUT_BLOCKED`, and `ENABLED_AND_DETECTING`. For cases when the detections are blocked, the `SdkStatus` is still available to get more information about what is blocking detections (e.g. insufficient permissions).

#### 7. Update Other Asynchronous Method Usages

Replace the usage of the following asynchronous SDK methods with their new `PendingOperation` returning counterparts:

|                 Deprecated Method                |       Replacement Method      |
| :----------------------------------------------: | :---------------------------: |
|               reset(ResetCallback)               |            reset()            |
|      getUserAccessToken(TokenResultCallback)     |    requestUserAccessToken()   |
| startTrip(Map, TransportMode, StartTripCallback) | startTrip(Map, TransportMode) |
|            stopTrip(StopTripCallback)            |           stopTrip()          |
|    submitDetections(SubmitDetectionsCallback)    |       submitDetections()      |

The new methods return a `PendingOperation` result which you can use to capture the operation's result.

#### 8. Update the Vehicle Crash Detection Code

Update the package name of the imported classes and utilize the `CrashDetectionApi` class to access the crash detection methods with their updated signatures. See [here](android.md#crash-detection). If you were using the deprecated crash detection methods from the `Sentiance` class, migrate to the new ones.

#### 9. Update Other Code Usages

* Replace the SDK status `isLocationPermGranted` field usage with `locationPermission`.&#x20;
* Replace `isInitialized()` usage with `getInitState()`.

## Migrating from 3.x to 4.x

{% hint style="info" %}
This update brings Android Oreo compatibility. You will now be able to target API level 26.
{% endhint %}

### SDK Initialization

Initializing the SDK is done by calling the [`init()`](../../api-reference/android/sentiance.md.md#init) method and passing an [`SdkConfig`](../../api-reference/android/sdkconfig/) object.[`SdkConfig.Builder`](../../api-reference/android/sdkconfig/sdkconfig-builder.md) now expects a notification as the 3rd parameter. `enableForeground(notification)` is no longer available for this purpose. The SDK will show a notification depending on the OS version, targeted API level, and remote app configuration.

### SDK Control

The `stopAfter(seconds)` method is no longer available.

### User Metadata

User metadata methods no longer accept `MetadataCallback` as a 3rd parameter. Adding and removing metadata is now done asynchronously via the payload submission system.

### External Events

Registering external events is no longer available.

### Trip Control

#### Starting and Stopping Trips

``[`startTrip()`](../../api-reference/android/sentiance.md.md#starttrip-map-transportmode-starttripcallback) and [`stopTrip()`](../../api-reference/android/sentiance.md.md#stoptrip-stoptripcallback) methods now require [`StartTripCallback`](../../api-reference/android/trip/starttripcallback.md) and [`StopTripCallback`](../../api-reference/android/trip/stoptripcallback.md) parameters respectively.

#### Trip Details

The SDK no longer returns a `Trip` object when a trip is stopped. The [`onTripTimeout()`](../../api-reference/android/trip/triptimeoutlistener.md#ontriptimeout)method of [`TripTimeoutListener`](../../api-reference/android/trip/triptimeoutlistener.md) no longer returns a `Trip` object. Similarly, the `onTripStopped()` method of [`StopTripCallback`](../../api-reference/android/trip/stoptripcallback.md) no longer exists. This interface now provides an [`onSuccess()`](../../api-reference/android/trip/stoptripcallback.md#onsuccess) and [`onFailure(sdkStatus)`](../../api-reference/android/trip/stoptripcallback.md#onfailure) methods.

#### Checking Ongoing Trips

The [`isTripOngoing()`](../../api-reference/android/sentiance.md.md#istripongoing) method now expects a parameter of type [`TripType`](../../api-reference/android/trip/triptype.md).

### Callbacks

All callback and listener methods are now executed on the application's main thread. If you perform any long running or network operations directly in the callbacks, please take care to move them to a background thread instead.

### Other

`getWiFiLastSeenTimestamp()` is no longer available.

The [`CrashCallback`](../../api-reference/android/crashdetection/crash-callback.md)'s Location parameter is now `@Nullable`.
