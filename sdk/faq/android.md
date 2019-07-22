# Android

### How big is the SDK library?

When including our SDK in your application, your application will grow by about 1 MB. When using the [native optimization version](../getting-started/android-sdk/include-sdk.md), there will be an additional 1.5 MB on top of this.

### What is the DEX method reference count?

Our SDK consumes about 8000 \(12%\) of the available 65,536 method reference count for a single dex file.

### What app permissions are required by the SDK?

Please see our list of [manifest permissions](../appendix/android/manifest-permission.md). The only permission that requires user consent is the location permission, and is mandatory for the proper operation of the SDK detections.

### I see a lot of missed trips and stationary moments in the timeline

Our SDK depends on proper device configuration in order to perform detections. Missed events can be due to the user disabling device location tracking, enabling airplane mode, or sometimes restricting the app's background execution. You can be notified of these changes by handling [SdkStatus](../api-reference/android/sdkstatus/) updates as shown [here](../getting-started/android-sdk/sdk-status-updates.md).

On some devices however, manufacturers tend to be very restrictive on background execution for newly installed apps. On these devices, the user has to manually whitelist the app to allow proper detections. A handy whitelisting guide can be found on [www.dontkillmyapp.com](www.dontkillmyapp.com). Also, have a look at our [battery optimization page](../appendix/android/android-battery-optimization.md) to learn how to ask the user to disable Android's battery optimization.

### Why does the SDK stay in PENDING state when running on an emulator?

The most common reason for this is that the network location provider is disabled, which means Android can obtain location data only via the GPS provider. Android normally has two location providers, GPS and network. On emulators, the network provider is usually disabled, and you can use the GPS provider to mock the device's location.

By default, our SDK requires the network provider to be enabled so that locations work indoors as well. This usually isn't a problem in the real world, as users normally have either both GPS and network providers enabled \(i.e. high accuracy mode\), or at least the network provider enabled \(i.e. battery saving mode\).

To overcome this problem on the emulator, first make sure this is the cause by checking the [`LocationSetting`](../api-reference/android/sdkstatus/#locationsetting) field of the [`SdkStatus`](../api-reference/android/sdkstatus/). If it shows `DEVICE_ONLY`, go the device's location settings and set the location mode to "high accuracy". On a Pixel emulator running Android Oreo and above, you may need to expand the "Advanced" section, choose "Google Location Accuracy" and toggle the "Improve Location Accuracy" off and on.

If this does not solve the problem, check the [`SdkStatus`](../api-reference/android/sdkstatus/) to see what other detection condition is not being satisfied.

