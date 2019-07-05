# Android

### How big is the SDK library?

When including our SDK in your application, your application will grow by about 1MB. When using the [native optimization version](../getting-started/android-sdk/include-sdk.md), there will be an additional 1.5 MB on top of this.

### What is the DEX method count?

Our SDK consumes about 8000 methods \(12%\) of the available 65,536 methods in a single dex file.

### What app permissions are required by the SDK?

Please see our list of [manifest permissions](../appendix/android/manifest-permission.md). The only permission that requires user consent is the location permission, and is mandatory for the proper operation of the SDK detections.

### I'm getting a version collision or mismatch error with a certain library

Our SDK has a dependency on the Google Play location services library, which itself has dependencies on various other support libraries. If your application has a dependency on a different version of a play services, support, or location library, it may result in version conflict.

To solve this, you may exclude the conflicting library from our SDK and include a higher version separately.

```groovy
// In this example, 'com.android.support' has a conflict.

implementation ('com.sentiance:sdk:4.4.0@aar') {
	transitive = true
	exclude group: 'com.android.support', module: 'support-v4'
}
```

### I see a lot of missed trips and stationary moments in the timeline

Our SDK depends on proper device configuration in order to perform detections. Missed events can be due to the user disabling device location tracking, enabling airplane mode, or sometimes restricting the app's background execution. You can be notified of these changes by handling [SdkStatus](../api-reference/android/sdkstatus/) updates as shown [here](../getting-started/android-sdk/sdk-status-updates.md).

On some devices however, manufacturers tend to be very restrictive on background execution for newly installed apps. On these devices, the user has to manually whitelist the app to allow proper detections. A handy whitelisting guide can be found on [www.dontkillmyapp.com](www.dontkillmyapp.com). Also, have a look at our [battery optimization page](../appendix/android/android-battery-optimization.md) to learn how to ask the user to disable Android's battery optimization.

### Why does the SDK stay in PENDING state when running on an emulator?

The most common reason for this is that the network location provider is disabled, which means Android can obtain location data only via the GPS provider. Android normally has two location providers, GPS and network. On emulators, the network provider is usually disabled, and you can use the GPS provider to mock the device's location.

By default, our SDK requires the network provider to be enabled so that locations work indoors as well. This usually isn't a problem in the real world, as users normally have either both GPS and network providers enabled \(i.e. high accuracy mode\), or at least the network provider enabled \(i.e. battery saving mode\).

To overcome this problem on the emulator, first make sure this is the cause by checking the [`LocationSetting`](../api-reference/android/sdkstatus/#locationsetting) field of the [`SdkStatus`](../api-reference/android/sdkstatus/). If it shows `DEVICE_ONLY`, go the device's location settings and set the location mode to "high accuracy". On a Pixel emulator running Android Oreo and above, you may need to expand the "Advanced" section, choose "Google Location Accuracy" and toggle the "Improve Location Accuracy" off and on.

If this does not solve the problem, check the [`SdkStatus`](../api-reference/android/sdkstatus/) to see what other detection condition is not being satisfied.

### Is the SDK compatible with AndroidX support libraries?

Our SDK depends on several `com.android.support` libraries. Therefore, if you've updated your app to use AndroidX support libraries, or you're using [the following](https://developers.google.com/android/guides/releases#june_17_2019) play services library versions \(or higher\), you must enable Jetifier to migrate the SDK's dependencies to the AndroidX equivalent ones. To do so, add the following lines to your project's gradle.properties file:

{% code-tabs %}
{% code-tabs-item title="gradle.properties" %}
```groovy
android.useAndroidX=true
android.enableJetifier=true
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Without this change, your build might fail with the following errors:

> Error while merging dex archives
>
> Error: Program type already present: android.support.v4.app.INotificationSideChannel

Or, if you've excluded the SDK's support library dependencies as described [here](android.md#im-getting-a-version-collision-or-mismatch-error-with-a-certain-library), SDK initialization will fail at runtime with the following error:

> NoClassDefFoundError: Failed resolution of: Landroid/support/v4/util/ArrayMap

