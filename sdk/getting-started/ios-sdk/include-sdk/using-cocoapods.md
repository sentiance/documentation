# Using CocoaPods

[CocoaPods](http://cocoapods.org/) is a dependency manager for Objective-C and Swift, which automates and simplifies the process of using 3rd-party libraries in your projects. See the [Get Started](http://cocoapods.org/#get\_started) section for more details.

{% hint style="warning" %}
Before starting to prepare for the installation, please make sure that **CocoaPods** **1.10.0** or above is installed on your machine.&#x20;
{% endhint %}

**Podfile**

If your project is already using CocoaPods, simply add these lines below in your podfile:

```
platform :ios, '12.0'

pod 'SENTSDK', '~>x.y.z'
```

You can obtain the latest version of our iOS SDK from our [changelog page](../../../changelog/ios.md).

<details>

<summary>Building for the arm64 (M1 Mac) simulator</summary>

The Sentiance SDK itself supports the arm64 simulator architecture. However, the SDK has a dependency on TensorFlow Lite v2.7.0, which does not support arm64 simulators. To address this limitation, use our custom TensorFlow Lite v2.7.0 framework. In your **Podfile**, add the following entry:

{% code title="Podfile" %}
```
pod 'TensorFlowLiteC', :podspec => 'https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC.podspec'
```
{% endcode %}

More information about this custom framework can be found on [this page](../../../appendix/ios/m1-simulator-support.md).

</details>

Run the following command from terminal:

```
pod install --repo-update
```

{% hint style="info" %}
The Sentiance SDK has a dependency on v2.7.0 of the TensorFlowLiteC framework, which does not support M1 Mac simulators. You can make use of our custom TensorFlowLite framework, to run your app on M1 Mac simulators. See [this page](../../../appendix/ios/m1-simulator-support.md).
{% endhint %}
