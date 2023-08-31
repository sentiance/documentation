# Installation with Carthage

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

[Carthage](https://github.com/Carthage/Carthage) is a dependency manager for Objective-C and Swift, which simplifies adding 3rd-party frameworks to your projects. See the [Quick Start](https://github.com/Carthage/Carthage#quick-start) section of Carthage github page for more details.

**Cartfile**

1. If your project is already using Carthage, simply add these lines below in your Cartfile.

```
binary "https://sentiance-u1-sdk-downloads.s3-eu-west-1.amazonaws.com/ios/carthage/SENTSDK.json"
```

&#x20;  2\. Then run the following command from Terminal.

```
carthage update
```

&#x20;  3\. A **Cartfile.resolved** file and a **Carthage** directory will appear in the same directory where your **.xcodeproj** or **.xcworkspace** is.

&#x20;  4\. Drag the built **.framework** binary from **Carthage/Build/** into _Link Binary With Libraries_ section under _Build Phases_ of your application target.

&#x20;  5\. On your application target's _Build Phases_ settings tab, click the _+_ icon and choose _New Run Script Phase_. Create a _Run Script_ in which you specify your shell (ex: /bin/sh), add the following contents to the script area below the shell:

```
/usr/local/bin/carthage copy-frameworks
```

&#x20;  6\. Depending on your Xcode setup, it might be required to add the following libraries: **libz.tbd (previously libz.dylib), CoreMotion, SystemConfiguration, CoreLocation, Foundation, CallKit, CoreTelephony, CoreData.**

&#x20;  ****   7. Update your project's [Build Settings](https://docs.sentiance.com/sdk/getting-started/ios-sdk/1.-installation/manual-installation#build-settings) and follow the [Usage](https://docs.sentiance.com/sdk/getting-started/ios-sdk/configuration) steps to start using the SDK in your project. ****&#x20;
