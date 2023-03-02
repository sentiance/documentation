# iOS Quick Start

{% hint style="danger" %}
If you are migrating from version 5.x to 6.x, please use our [migration guide](../../appendix/migration-guide/ios.md#migrating-from-5.x-to-6.x) instead of this quick start guide.&#x20;
{% endhint %}

{% hint style="success" %}
### Platform requirements

* The Sentiance SDK requires iOS 13.0 or higher. Apps should be built with the latest iOS SDK provided by Apple/Xcode.
* Building and running your app on M1 Mac simulators is possible with the use of our [custom TensorFlow Lite framework](../../appendix/ios/m1-simulator-support.md).
* List of all support architectures can be found [here](../../appendix/ios/supported-ios-versions-and-architectures.md).
{% endhint %}

{% hint style="success" %}
### Dependency requirements

The Sentiance SDK has the following external library dependencies. If your app depends on versions other than the ones mentioned here, please reach out to us to address possible incompatibility issues.

* **TensorFlowLiteC**: v2.7.0
* **Protobuf**: v3.18
* **UnzipKit**: v1.9
{% endhint %}

If you want to get started quickly, you can check out our [sample application](https://github.com/sentiance/sample-apps-ios). If you prefer to integrate the SDK in your existing app, read on.
