# Installation with CocoaPods

[CocoaPods](http://cocoapods.org/) is a dependency manager for Objective-C and Swift, which automates and simplifies the process of using 3rd-party libraries in your projects. See the [Get Started](http://cocoapods.org/#get_started) section for more details.

**Podfile**

If your project is already using CocoaPods, simply add these lines below in your podfile:

```
platform :ios, '9.0'
pod 'SENTSDK'
```

Then run the following command from Terminal:

```
pod install
```



You'll also need to include the SDK bundle in your project:

1. Go to the **Build Phases** tab of your target settings
2. Expand the **Copy Bundle Resources** row and click the **+** button
3. Choose the **SENTSDK.bundle** file located inside **SENTSDK.framework**

