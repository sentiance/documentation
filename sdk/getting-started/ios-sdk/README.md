# iOS Quick Start

{% hint style="success" %}
### Platform requirements

The Sentiance SDK requires iOS 13.0 or higher. Apps should be built with the latest iOS SDK provided by Apple/Xcode.

Building and running your app on M1 Mac simulators is possible with the use of our [custom TensorFlow Lite framework](../../appendix/ios/m1-simulator-support.md). List of all support architectures can be found [here](../../appendix/ios/supported-ios-versions-and-architectures.md).
{% endhint %}

{% hint style="success" %}
### Dependency requirements

#### TensorFlow Lite

The Sentiance SDK uses version 2.7.0 of the TensorFlow Lite library. If your app depends on a different version, please reach out to Sentiance to address possible incompatibility issues.

#### Protobuf

The Sentiance SDK uses Protobuf version 3.18.

#### UnzipKit

The Sentiance SDK uses UnzipKit version 1.9.
{% endhint %}

If you want to get started quickly, you can check out our [sample application](https://github.com/sentiance/sample-apps-ios). If you prefer to integrate the SDK in your existing app, read on.
