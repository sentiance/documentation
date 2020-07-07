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
pod install --repo-update
```

