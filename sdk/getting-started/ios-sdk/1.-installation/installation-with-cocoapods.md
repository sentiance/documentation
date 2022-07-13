# Installation with CocoaPods

[CocoaPods](http://cocoapods.org/) is a dependency manager for Objective-C and Swift, which automates and simplifies the process of using 3rd-party libraries in your projects. See the [Get Started](http://cocoapods.org/#get\_started) section for more details.

{% hint style="warning" %}
Before starting to prepare for the installation, please make sure that **CocoaPods** **1.10.0** or above is installed on your machine.&#x20;
{% endhint %}

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

{% hint style="info" %}
The Sentiance SDK has a dependency on v2.7.0 of the TensorFlowLiteC framework, which does not support M1 Mac simulators. You can make use of our custom TensorFlowLite framework, to run your app on M1 Mac simulators. See [this page](../../../appendix/ios/m1-simulator-support.md).
{% endhint %}
