# Using Carthage

[Carthage](https://github.com/Carthage/Carthage) is a dependency manager for Objective-C and Swift, which simplifies adding 3rd-party frameworks to your projects. See the [Quick Start](https://github.com/Carthage/Carthage#quick-start) section of Carthage github page for more details.

### Steps

1. If your project is already using Carthage, simply add these lines below in your Cartfile.

```
binary "https://sentiance-u1-sdk-downloads.s3-eu-west-1.amazonaws.com/ios/carthage/SENTSDK.json"
```

&#x20;2\. Then run the following command from Terminal.

```
carthage update --use-xcframeworks
```

A **Cartfile.resolved** file and a **Carthage** directory will appear in the same directory where your **.xcodeproj** or **.xcworkspace** is.

3\. Drag the built **.xcframework** binary from **Carthage/Build/** into _Frameworks, Libraries and Embedded content_ section under _General_ tab of your application target.

4\. Depending on your Xcode setup, it might be required to add the following libraries: libz.tbd (previously libz.dylib), CoreMotion, SystemConfiguration, CoreLocation, Foundation, CallKit, CoreTelephony, CoreData.

5\. Follow [steps 3, 4, and 5](manual-integration.md#manual-integration-step-3) of the manual integration guide.

6\. Continue to the [Project settings](../project-settings.md) step.

