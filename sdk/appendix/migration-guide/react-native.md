# React Native

## Migrating from 4.x to 6.x

This is a guide for migrating from the v4.x to v6.x of the Sentiance React Native SDKs. Aside from the new features that this version brings, one noticeable change is the variety of modules that have been introduced to replace the monolithic `react-native-sentiance` module.&#x20;

These are smaller, independent modules that are distributed as their own packages. This has a number of advantages, such as smaller app bundle sizes (since you only install the modules you need).&#x20;

This section describes all the changes that were made since version 4.7.0, and provides two code migration paths: a minimal one that utilizes existing (but deprecated) APIs, and a full one that utilizes only the new APIs.

### General Changes

#### Introducing new SDK modules

Version 6.x breaks down the monolithic `react-native-sentiance` module into several new modules, such as `core` , `crash-detection` and others. These new modules are now part of the **@sentiance-react-native** scope on NPM.

Among the new modules introduced, we also included a `legacy` module.&#x20;

This module provides the same APIs and functionality that the deprecated `react-native-sentiance` does. Using this module would allow you to migrate from v4 to v6 of the React Native SDKs with minimal effort.

{% hint style="info" %}
Please note that new SDK features and functionality will be supported via the new SDK modules that have been introduced. As such, using the **legacy** module is discouraged. Instead, you are encouraged to do a full migration, in order to benefit from upcoming features and improvements.
{% endhint %}

The `@sentiance-react-native/core` module contains functionality that is needed by all other modules, and hence must be installed always.

#### Java 8 Compatibility on Android

Version 6.x makes use of Java 8 language features. Make sure your app is configured to support Java 8. See [this](https://developer.android.com/studio/write/java8-support#supported\_features) guide.

#### iOS Pod Update

The iOS pod has changed from `RNSentiance` to `RNSentianceCore`, along with a new podspec file located under `../node_modules/react-native-sentiance/ios`.

### Code Changes & Deprecations

Below is the list of deprecations and code changes that were made in 6.x.

#### SDK Native Event Names

The following SDK events have been renamed, to help make the names even more unique and avoid any potential clashes with other components or libraries transmitting events with the same name.

|        Old Name       |                 New Name                 |
| :-------------------: | :--------------------------------------: |
|    SDKStatusUpdate    |     SENTIANCE\_STATUS\_UPDATE\_EVENT     |
|      SDKUserLink      |       SENTIANCE\_USER\_LINK\_EVENT       |
| SDKUserActivityUpdate | SENTIANCE\_USER\_ACTIVITY\_UPDATE\_EVENT |
|     SDKTripTimeout    |  SENTIANCE\_ON\_TRIP\_TIMED\_OUT\_EVENT  |
|   VehicleCrashEvent   |     SENTIANCE\_VEHICLE\_CRASH\_EVENT     |

In addition, the **SDKCrashEvent** and **SDKTripProfile** events have been removed.

#### New SDK Modules

v6 introduces several new modules that provide Sentiance functionality:

* **legacy**: this module was introduced to make it easier for apps to integrate v6 with very minimal changes required. It provides all of the functionality previously provided by v4, but several APIs have been deprecated, and it no longer supports the old SDK event names. Please refer to the table above for a complete list of the changes in SDK event names.
* **core**: this module provides core Sentiance functionality, such as user creation and SDK detections. It serves as a base for all other modules, and hence must be installed always.
* **crash-detection**: this module provides crash detection related functionality.
* **user-context**: this module provides functionality to add user context awareness to your apps.

{% hint style="info" %}
Note that all deprecated functionality is now provided by the **legacy** module, and all of the new functionality introduced here is provided by the **core** module (except for crash detection related functionality, which is provided by the **crash-detection** module).
{% endhint %}

#### SDK Initialization & User Creation

The `init` and `initWithUserLinkingEnabled` functions have been deprecated.&#x20;

User creation is no longer a part of the SDK initialization process, **hence we expect apps to initialize the SDK natively during app startup, without postponing or delaying it.**&#x20;

This initializer can safely be called when a Sentiance user does not exist yet, as it will only do minimal work to prepare the SDK for user creation - **It will not create a new user.** Instead, if a Sentiance user already exists, it initializes the SDK internally and resumes detections (if detections were enabled in the past).

{% hint style="warning" %}
As long as a Sentiance user exists on the device, you are expected to initialize the SDK during app startup, without delay or postponement. If you intend to not run detections for a brief period, simply call `disableDetections` instead. **** If you intend to not run detections for a longer duration, simply reset the SDK to remove the user from the device.
{% endhint %}

* To create a Sentiance user, we have added a new function called `createUser`. You can use this method to create a Sentiance user anywhere in your app. Note that you can only create one user at any time. To create a different user, you must first reset the SDK.
* We have introduced an easier and a cleaner way to create users, using an authentication code instead of Sentiance credentials (app ID & secret). This is now the preferred way to create Sentiance users. See [this page](../user-creation.md) for more info.
* The `isNativeInitializationEnabled`, `enableNativeInitialization`, `disableNativeInitialization` functions have been deprecated.

#### Checking User Existence & Linking Status

You can use the new `userExists()` function to find out whether a Sentiance user already exists on the device, and to check whether the user has been successfully linked (i.e. user linking), you can call `isUserLinked()`.

These two functions can be called without having to initialize the SDK beforehand.

#### User Linking

* After creating an unlinked Sentiance user, you can link it at a later time by calling the new `linkUser` or `linkUserWithAuthCode` functions.
* The `isThirdPartyLinked` function has been deprecated. Use `isUserLinked` instead.
* The `userLinkCallback` function has been deprecated. You would call this function originally to let the Sentiance SDK know if user linking on your backend was successful or not. Instead, with the new user creation approach, the linker function you supply must return a boolean indicating the result of the user linking.

#### Enabling/Disabling detections

* The `start` function was deprecated in favour of `enableDetections`
* The `startWithStopDate` function was deprecated in favour of `enableDetectionWithExpiryDate`
* The `stop` function was deprecated in favour of `disableDetections`

#### SDK reset

The existing `reset` function that returns a `Promise<boolean>` has been deprecated. A new `reset` function that has been added returns a `Promise<ResetResult>` instead.

#### SDK status

* The `startStatus` field has been deprecated. The new `detectionStatus` field has been added as its successor.
* A `backgroundRefreshStatus` field has been added. (iOS only)
* A `addSdkUserActivityUpdateListener` function has been added. It registers a listener internally to the `SENTIANCE_STATUS_UPDATE_EVENT` event and notifies the caller of any SDK status updates.&#x20;

#### User access token

The `getUserAccessToken` function has been deprecated in favour of `requestUserAccessToken`.

#### User metadata fields

The existing `addUserMetadataField`, `addUserMetadataFields`, `removeUserMetadataField` functions return a `Promise<boolean>`. This boolean did not provide any additional information regarding whether the function call succeeded or not, and so we deprecated these functions in favour of new ones that return a `Promise<void>`.

#### Battery optimization

The existing `disableBatteryOptimization` function returns a `Promise<boolean>`. This boolean did not provide any additional information regarding whether the function call succeeded or not, and so we deprecated this function in favour of a new one that returns a `Promise<void>`.

#### User activity updates

In order to get user activity updates, you would call `listenUserActivityUpdates` originally to express your interest in getting user activity updates, before manually registering a listener to the now-deprecated `SDKUserActivityUpdate` event to process the actual updates.&#x20;

We added a new function, `addSdkUserActivityUpdateListener` that combines the two aforementioned actions into one.

#### Trips

* In order to be notified of a trip timeout, you would call `listenTripTimeout` originally to express your interest in being notified of trip timeout events, before manually registering a listener to the now-deprecated `SDKTripTimeout` event to process the actual timeout event. We added a new function, `addTripTimeoutListener` that combines the two aforementioned actions into one.
* The `startTrip` function that returns a `Promise<boolean>` was deprecated in favour of a new one that returns a `Promise<void>`.
* The `stopTrip` function that returns a `Promise<boolean>` was deprecated in favour of a new one that returns a `Promise<void>`.

#### Crash detection

* We moved the following, crash detection related functionality to the **crash-detection** module (but it's still available through the **legacy** module as well):
  * `listenVehicleCrashEvents`
  * `invokeDummyVehicleCrash`
  * `isVehicleCrashDetectionSupported`
*   In order to be notified of new crash events, you would call `listenVehicleCrashEvents`

    originally to express your interest in being notified of crash events, before manually registering a listener to the now-deprecated `VehicleCrashEvent` event to process the event. We added a new function, `addVehicleCrashEventListener` that combines the two aforementioned actions into one.

#### SDK notification

When running in the background, the Sentiance SDK needs to start a foreground service and supply a notification to Android, which gets shown to the user when the service is running.&#x20;

On Android, you could customize this notification via the **AndroidManifest.xml** file by specifying custom meta-data entries. The prefix to the names of these entries has changed from `com.sentiance.react.bridge` to `com.sentiance.react.bridge.core` .

In addition, we added a new field called **notification\_id** that allows you to configure the identifier of the SDK's notification.

#### Deprecated functions

Below is a summary of all the functions that have been deprecated (**v4.7.0** and below), and their new counterparts from the `core` module:

|                                                                         Deprecated function                                                                         |                                                                                    Replacement function                                                                                   |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                             <pre class="language-javascript"><code class="lang-javascript">start(): Promise&#x3C;SdkStatus></code></pre>                            |                        <pre class="language-javascript"><code class="lang-javascript">enableDetections(): Promise&#x3C;EnableDisableDetectionsResult></code></pre>                        |
|        <pre class="language-javascript"><code class="lang-javascript">startWithStopDate(stopEpochTimeMs: number | null): Promise&#x3C;SdkStatus></code></pre>       | <pre class="language-javascript"><code class="lang-javascript">enableDetectionsWithExpiryDate(expiryEpochTimeMs: number | null): Promise&#x3C;EnableDisableDetectionsResult></code></pre> |
|                              <pre class="language-javascript"><code class="lang-javascript">stop(): Promise&#x3C;boolean></code></pre>                              |                        <pre class="language-javascript"><code class="lang-javascript">disableDetections(): Promise&#x3C;EnableDisableDetectionsResult></code></pre>                       |
|                              <pre class="language-javascript"><code class="lang-javascript">reset(): Promise&#x3C;boolean></code></pre>                             |                                       <pre class="language-javascript"><code class="lang-javascript">reset(): Promise&#x3C;ResetResult></code></pre>                                      |
|                   <pre class="language-javascript"><code class="lang-javascript">getUserAccessToken(): Promise&#x3C;UserAccessToken></code></pre>                   |                            <pre class="language-javascript"><code class="lang-javascript">requestUserAccessToken(): Promise&#x3C;UserAccessToken></code></pre>                            |
|        <pre class="language-javascript"><code class="lang-javascript">addUserMetadataField(label: string, value: string): Promise&#x3C;boolean></code></pre>        |                     <pre class="language-javascript"><code class="lang-javascript">addUserMetadataField(label: string, value: string): Promise&#x3C;void></code></pre>                    |
|          <pre class="language-javascript"><code class="lang-javascript">addUserMetadataFields(metadata: MetadataObject): Promise&#x3C;boolean></code></pre>         |                        <pre class="language-javascript"><code class="lang-javascript">addUserMetadataFields(label: MetadataObject): Promise&#x3C;void></code></pre>                       |
|              <pre class="language-javascript"><code class="lang-javascript">removeUserMetadataField(label: string): Promise&#x3C;boolean></code></pre>              |                           <pre class="language-javascript"><code class="lang-javascript">removeUserMetadataField(label: string): Promise&#x3C;void></code></pre>                          |
|                   <pre class="language-javascript"><code class="lang-javascript">disableBatteryOptimization(): Promise&#x3C;boolean></code></pre>                   |                                <pre class="language-javascript"><code class="lang-javascript">disableBatteryOptimization(): Promise&#x3C;void></code></pre>                               |
|                    <pre class="language-javascript"><code class="lang-javascript">listenUserActivityUpdates(): Promise&#x3C;boolean></code></pre>                   |                                <pre class="language-javascript"><code class="lang-javascript">listenUserActivityUpdates(): Promise&#x3C;void></code></pre>                                |
| <pre class="language-javascript"><code class="lang-javascript">startTrip(metadata: MetadataObject | null,  hint: TransportMode): Promise&#x3C;boolean></code></pre> |              <pre class="language-javascript"><code class="lang-javascript">startTrip(metadata: MetadataObject | null, hint: TransportMode): Promise&#x3C;void></code></pre>              |
|                            <pre class="language-javascript"><code class="lang-javascript">stopTrip(): Promise&#x3C;boolean></code></pre>                            |                                         <pre class="language-javascript"><code class="lang-javascript">stopTrip(): Promise&#x3C;void></code></pre>                                        |
|                        <pre class="language-javascript"><code class="lang-javascript">submitDetections(): Promise&#x3C;boolean></code></pre>                        |                                     <pre class="language-javascript"><code class="lang-javascript">submitDetections(): Promise&#x3C;void></code></pre>                                    |
|       <pre class="language-javascript"><code class="lang-javascript">updateSdkNotification(title: string, message: string): Promise&#x3C;boolean></code></pre>      |                   <pre class="language-javascript"><code class="lang-javascript">updateSdkNotification(title: string, message: string): Promise&#x3C;void></code></pre>                   |
|                       <pre class="language-javascript"><code class="lang-javascript">isThirdPartyLinked(): Promise&#x3C;boolean></code></pre>                       |                                     <pre class="language-javascript"><code class="lang-javascript">isUserLinked(): Promise&#x3C;boolean></code></pre>                                     |

Most of the changes to the functions in the table above concern mainly their return values. Several functions returned a `Promise` that resolves to a `boolean` that does not add any useful information regarding whether the function call was successful or not. Their new counterparts return a `Promise` that resolves to `void` instead. To catch any errors, use a try/catch mechanism.

The following the functions have also been deprecated:

|                                                                                                                 Deleted functions                                                                                                                |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                                                <pre class="language-javascript"><code class="lang-javascript">getValueForKey(key: string, defaultValue: string): Promise&#x3C;string></code></pre>                                               |
|                                                           <pre class="language-javascript"><code class="lang-javascript">setValueForKey(key: string, value: string): void</code></pre>                                                           |
|                                                        <pre class="language-javascript"><code class="lang-javascript">isNativeInitializationEnabled(): Promise&#x3C;boolean></code></pre>                                                        |
|                                                          <pre class="language-javascript"><code class="lang-javascript">enableNativeInitialization(): Promise&#x3C;boolean></code></pre>                                                         |
|                                                         <pre class="language-javascript"><code class="lang-javascript">disableNativeInitialization(): Promise&#x3C;boolean></code></pre>                                                         |
|             <pre class="language-javascript"><code class="lang-javascript">init(
    appId: string,  
    secret: string,  
    baseURL: string | null,  
    shouldStart: boolean): Promise&#x3C;boolean | SdkStatus>;</code></pre>             |
| <pre class="language-javascript"><code class="lang-javascript">initWithUserLinkingEnabled(  
    appId: string,  
    secret: string,  
    baseURL: string | null,  
    shouldStart: boolean): Promise&#x3C;boolean | SdkStatus>;</code></pre> |

In addition to the functions listed above, the following functions (provided by the **v4.7.1** and above) were also deprecated:

|                                                             Deprecated function                                                            |                                                                                               Replacement function                                                                                              |
| :----------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| <pre class="language-javascript"><code class="lang-javascript">createUserExperimental(configuration: CreateUserConfiguration)</code></pre> |                               <pre class="language-javascript"><code class="lang-javascript">createUser(options: UserCreationOptions): Promise&#x3C;CreateUserResult></code></pre>                              |
|                    <pre class="language-javascript"><code class="lang-javascript">resetExperimental(): void</code></pre>                   |                                                  <pre class="language-javascript"><code class="lang-javascript">reset(): Promise&#x3C;ResetResult></code></pre>                                                 |
|            <pre class="language-javascript"><code class="lang-javascript">disableExperimental(): Promise&#x3C;void></code></pre>           | <pre class="language-javascript"><code class="lang-javascript">disableDetections(): Promise&#x3C;EnableDisableDetectionsResult>In addition, the following the functions have also been deprecated:</code></pre> |
|            <pre class="language-javascript"><code class="lang-javascript">enableExperimental() : Promise&#x3C;void></code></pre>           |                                   <pre class="language-javascript"><code class="lang-javascript">enableDetections(): Promise&#x3C;EnableDisableDetectionsResult></code></pre>                                   |

### **Minimal Migration Steps (only for v4.7.0 and below)**

The following describes the minimal changes that you have to do, in order to compile and run your app with v6.x of the Sentiance SDK. Depending on your development environment and integration method, you might need to make additional changes that are not mentioned here. If you haven't already done so, please go through the [General Changes](react-native.md#general-changes) section in order to get a complete list of the changes that were made in version 6.x.

Please note that it is only possible to do a minimal migration if you are using v4.7.0 or below of the Sentiance React Native SDK. If you are using a higher version, then you need to perform a [full migration](react-native.md#full-migration-steps).

#### 1. Remove v4 from your code

Start by removing the `react-native-sentiance` dependency from your project's **package.json** file. You can do so by running the following command on your project's root folder:

```bash
npm uninstall react-native-sentiance
```

Or you can remove the dependency manually by editing your **package.json**:

{% code title="package.json" %}
```json
{
  ...,
  "dependencies": {
    ...,
    "react-native-sentiance": "^4.x.x" <-- Remove this line
  }
}
```
{% endcode %}

To remove the package from your local environment, delete the `yarn.lock`/`package-lock.json` files then reinstall the project's dependencies.

Next, you need to remove all references to the v4 SDK from your Android code. To do that, follow these steps:

* Open up your project's **android/settings.gradle** file. There are 2 lines in there that need to be removed:

{% code title="android/settings.gradle" %}
```groovy
rootProject.name = 'YourProjectName'

// Remove the 2 lines below
include ':react-native-sentiance'
project(':react-native-sentiance').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-sentiance/android')

include ':app'
```
{% endcode %}

* Open your project's **android/app/build.gradle** file, and remove the `react-native-sentiance` dependency:

{% code title="android/app/build.gradle" %}
```groovy
dependencies {
    ...
    implementation project(':react-native-sentiance') // Remove this line
}
```
{% endcode %}

#### 2. Add v6 dependency

Run:

```bash
npm install @sentiance-react-native/core @sentiance-react-native/legacy
```

#### 3. Update your iOS Podfile

Replace the following line:

```
pod 'RNSentiance', :path => '../node_modules/react-native-sentiance/ios/RNSentiance.podspec'
```

with:

```
pod 'RNSentianceCore', :path => '../node_modules/@sentiance-react-native/core/ios'
```

and then run `pod install` from within your project's **ios/** directory.

#### 4. Update your Javascript imports

Replace all occurrences of this import in your code:

```javascript
import RNSentiance from 'react-native-sentiance';
```

with the following:

```javascript
import RNSentiance from '@sentiance-react-native/legacy';
```

#### 5. Update the Sentiance SDK event names

Refer to this [section](react-native.md#sdk-native-event-names) for more details on the changes to the SDK event names. Make sure to replace every occurrence of the old event names with their corresponding new ones.

#### 6. Update the AndroidManifest.xml file

When running in the background, the Sentiance SDK needs to start a foreground service and supply a notification to Android, which gets shown to the user when the service is running.&#x20;

On Android, you could customize this notification via the **AndroidManifest.xml** file by specifying custom meta-data entries. The prefix to the names of these entries has changed from `com.sentiance.react.bridge` to `com.sentiance.react.bridge.core`. Make sure to update your code accordingly.

### Full Migration Steps

The following steps describe all the changes that you have to do, in order to replace deprecated Sentiance API usage with non-deprecated counterparts, and successfully compile and run your app after updating to v6.x. Depending on your development environment and integration method, you might need to make additional changes that are not mentioned here. If you haven't already done so, please go through the [General Changes](react-native.md#general-changes) section in order to get a complete list of the changes that were made in version 6.x.

#### 1. Remove v4 from your code

Start by removing the `react-native-sentiance` dependency from your project's **package.json** file. You can do so by running the following command on your project's root folder:

```shell
npm uninstall react-native-sentiance
```

Or you can remove the dependency manually by editing your **package.json**:

{% code title="package.json" %}
```json
{
  ...,
  "dependencies": {
    ...,
    "react-native-sentiance": "^4.x.x" <-- Remove this line
  }
}
```
{% endcode %}

To remove the package from your local environment, delete the `yarn.lock`/`package-lock.json` files then reinstall the project's dependencies.

Next, you need to remove all references to the v4 SDK from your Android code. To do that, follow these steps:

* Open up your project's **android/settings.gradle** file. There are 2 lines in there that need to be removed:

{% code title="android/settings.gradle" %}
```groovy
rootProject.name = 'YourProjectName'

// Remove the 2 lines below
include ':react-native-sentiance'
project(':react-native-sentiance').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-sentiance/android')

include ':app'
```
{% endcode %}

* Open your project's **android/app/build.gradle** file, and remove the `react-native-sentiance` dependency:

{% code title="android/app/build.gradle" %}
```groovy
dependencies {
    ...
    implementation project(':react-native-sentiance') // Remove this line
}
```
{% endcode %}

#### 2. Add v6 dependency

Run:

```bash
npm install @sentiance-react-native/core @sentiance-react-native/crash-detection
```

#### 3. Update your iOS Podfile

Replace the following line:

```
pod 'RNSentiance', :path => '../node_modules/react-native-sentiance/ios/RNSentiance.podspec'
```

with:

```
pod 'RNSentianceCore', :path => '../node_modules/@sentiance-react-native/core/ios'
```

and then run `pod install` from within your project's **ios/** directory.

#### 4. Update your Javascript imports

The previous version of the Sentiance React Native SDK provided the following crash-detection related functionality:

* `listenVehicleCrashEvents`
* `invokeDummyVehicleCrash`
* `isVehicleCrashDetectionSupported`

These functions have been moved into a separate module, called `crash-detection`.&#x20;

Make sure to add the proper import everywhere you use these 3 functions; you can proceed in one of two ways:

```javascript
// 1. Import default
import SentianceCrashDetection from '@sentiance-react-native/crash-detection';
await SentianceCrashDetection.listenVehicleCrashEvents();
await SentianceCrashDetection.invokeDummyVehicleCrash();
const isCrashDetectionSupported = 
    await SentianceCrashDetection.isVehicleCrashDetectionSupported();

// 2. or use named imports
import {
    listenVehicleCrashEvents,
    invokeDummyVehicleCrash,
    isVehicleCrashDetectionSupported
} from '@sentiance-react-native/crash-detection';
```

The rest of the Sentiance SDK functionality that your integration uses is now provided by the `core` module. Make sure to replace all of this import's occurrences in your code:

```javascript
import RNSentiance from 'react-native-sentiance';
```

with the following:

```javascript
import RNSentiance from '@sentiance-react-native/core';
```

#### 5. Update the SDK initialization

In your existing integration, you may be initializing the Sentiance SDK in different ways:

1. By calling `init` in your Javascript code to initialize the SDK and to create a user without linking it.
2. By calling `initWithUserLinkingEnabled` in your Javascript code to initialize the SDK and to create a linked user.
3. By calling a helper function from the now-deprecated `RNSentianceHelper` class in your Android code

The Sentiance SDK must be initialized natively, as Javascript initialization is no longer supported. Remove any calls to `init` or `initWithUserLinkingEnabled` from your Javascript code.&#x20;

For Android, replace any calls through the `RNSentianceHelper` class with a call to the new `initializeSDK` method available in the new `SentianceHelper` class:

{% code title="MainApplication.java" %}
```java
import com.sentiance.react.bridge.core.SentianceHelper;

// Inside the onCreate method
SentianceHelper.getInstance(getApplicationContext())
    .initializeSDK();
```
{% endcode %}

For iOS, replace the call to `initSDK:secret:baseURL:shouldStart:resolver:rejecter:` with `initializeSDKWithLaunchOptions:` that is now available via the `RNSentianceHelper` class. If you previously had `shouldStart` set to `YES`, then call `enableDetectionsIfUserExists` after a successful initialization to enable detections. Note that this last step is not required for completely new integrations, as enabling SDK detections [is now persistent](ios.md#4.-enable-detections).

{% code title="AppDelegate.m" %}
```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    ...
    BOOL shouldStart = YES; // this is normally YES, but check your existing implementation

    RNSentianceHelper *helper = [[RNSentianceHelper alloc] init];
    SENTInitializationResult *result = [helper initializeSDKWithLaunchOptions:launchOptions];
    if (result.isSuccessful && shouldStart) {
        [helper enableDetectionsIfUserExists];
    }
    
    return YES;
}
```
{% endcode %}

{% hint style="info" %}
If you are using the experimental methods for integrating the SDK, the ones introduced in v4.7.1, alongside `initializeWithSuccess:failure:`, then replace it with the initializer method that is mentioned above. In this case, you should consider `shouldStart` to be `YES`.
{% endhint %}

Finally, enabling/disabling the native initialization is no longer supported. Make sure to remove any calls to the old `enableNativeInitialization`, `disableNativeInitialization`, `isNativeInitializationEnabled` functions from your code.

#### 6. Update the user creation process

In your existing integration, you will likely have some conditional logic that calls `init` or `initWithUserLinkingEnabled` in order to create a Sentiance user.

* If you are using `init`, then replace:

{% code title="app.js" %}
```javascript
await RNSentiance.init(
    APP_ID, 
    APP_SECRET, 
    SENTIANCE_PLATFORM_URL, 
    ...);
```
{% endcode %}

with the following:

```javascript
import { createUser } from '@sentiance-react-native/core';

await createUser(
    {
        appId: APP_ID,
        appSecret: APP_SECRET,
        platformUrl: SENTIANCE_PLATFORM_URL,
    }
);
```

* If you are using `initWithUserLinkingEnabled` to create a user, then replace:

{% code title="app.js" %}
```javascript
const emitter = new NativeEventEmitter(RNSentiance);

emitter.addListener('SDKUserLink',
      async data => {
        const { installId } = data;
        const success = await linkUserToYourBackend(installId);
        RNSentiance.userLinkCallback(success);
      }
    );

await RNSentiance.initWithUserLinkingEnabled(
    APP_ID, 
    APP_SECRET, 
    SENTIANCE_PLATFORM_URL, 
    ...);
```
{% endcode %}

with the following:

```javascript
import { createUser } from '@sentiance-react-native/core';

await createUser(
    {
        appId: APP_ID,
        appSecret: APP_SECRET,
        platformUrl: SENTIANCE_PLATFORM_URL,
        linker: async (installId) => {
            // This linker function must return a boolean, indicating if user 
            // linking to your backend was successful or not.
            return await linkUserToYourBackend(installId);
        }
    }
);
```

You no longer need to register an event listener onto **SDKUserLink** events or call `RNSentiance.userLinkCallback()`.

{% hint style="info" %}
**User Creation Without the Need for App Credentials**

In addition to the user-linker based approach of creating users, we have introduced an improved linked-user creation mechanism, which replaces the Sentiance app credentials with a temporary authentication code, obtained from Sentiance at the moment of user creation. This is our recommended approach for creating users in all new integrations. You can read more about it [here](../user-creation.md).
{% endhint %}

For more information on user creation, check out [this](../user-creation.md) page.

#### 7. Update the AndroidManifest.xml file

When running in the background, the Sentiance SDK needs to start a foreground service and supply a notification to Android, which gets shown to the user when the service is running.&#x20;

On Android, you could customize this notification via the **AndroidManifest.xml** file by specifying custom meta-data entries. The prefix to the names of these entries has changed from `com.sentiance.react.bridge` to `com.sentiance.react.bridge.core`. Make sure to update your code accordingly.

#### 8. Update the Sentiance SDK event names

Refer to this [section](react-native.md#sdk-native-event-names) for more details on the changes to the SDK event names. Make sure to replace every occurrence of the old event names with their corresponding new ones.

#### 9. Update other deprecated function usages

Refer to this [section](react-native.md#deprecated-functions) to view the full list of functions that have been deprecated, and make sure to replace the existing usage of the deprecated functions on that list with their new counterparts.

#### 10. Additional required changes (only if you are migrating from v4.7.1+)

* The `createUserExperimental` function has been deprecated. Use `createUser` instead:

```javascript
// Replace this code
import { createUserExperimental } from 'react-native-sentiance/sentiance';

await createUserExperimental(
    {
        appId: APP_ID,
        appSecret: APP_SECRET,
        baseUrl: SENTIANCE_PLATFORM_URL,
        linker: (data, isUserLinkingSuccessful) => {
            const { installId } = data;
            const success = await linkUserToYourBackend(installId);
            isUserLinkingSuccessful(success);
        }
    }
);

// With this code
import { createUser } from '@sentiance-react-native/core';

await createUser(
    {
        appId: APP_ID,
        appSecret: APP_SECRET,
        platformUrl: SENTIANCE_PLATFORM_URL,
        linker: installId => {
            // This linker function must return a boolean, indicating if user 
            // linking to your backend was successful or not.
            return await linkUserToYourBackend(installId);
        }
    }
);
```

* The `resetExperimental` function has been deprecated. Use `reset` instead:

```javascript
// Replace this code
import { resetExperimental } from 'react-native-sentiance/sentiance';
resetExperimental();

// With this code
import { reset } from '@sentiance-react-native/core';
const result = await reset();
```

* The `disableExperimental` function has been deprecated. Use `disableDetections` instead:

```javascript
// Replace this code
import { disableExperimental } from 'react-native-sentiance/sentiance';
await disableExperimental();

// With this code
import { disableDetections } from '@sentiance-react-native/core';
const result = await disableDetections();
```

* The `enableExperimental` function has been deprecated. Use `enableDetections` instead:

```javascript
// Replace this code
import { enableExperimental } from 'react-native-sentiance/sentiance';
await enableExperimental();

// With this code
import { enableDetections } from '@sentiance-react-native/core';
const result = await enableDetections();
```
