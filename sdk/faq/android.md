# Android

### How big is the SDK library?

When including our SDK in your application, your application will grow by about 1MB. When using the native [optimization version](../getting-started/android-sdk/include-sdk.md), there will be an additional 1.5 MB on top of this.

### What is the DEX method count?

Our SDK consumes about 8000 methods \(12%\) of the available 65,536 methods in a single dex file.

### I'm getting version collision error with the certain library

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

Our SDK depends on proper device configuration in order to do detections. Missed events can be due to the user disabling the device location mode, enabling airplane mode, or sometimes restricting the app's background execution. You can be notified of these changes by handling [SdkStatus](../api-reference/android/sdkstatus/) updates as shown [here](../getting-started/android-sdk/sdk-status-updates.md).

On some devices however, manufacturers tend to be very restrictive on background execution for newly installed apps. On these devices, the user has to manually whitelist the app to allow proper detections. A handy whitelisting guide can be found on [www.dontkillmyapp.com](www.dontkillmyapp.com).

