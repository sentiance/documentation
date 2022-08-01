# M1 Simulator Support

It's possible to build your Sentiance integrated app for the M1 Mac Simulator.

The SDK framework includes support for the arm64 simulator architecture, which is the target architecture for the M1 Mac simulator. However, the SDK has a dependency on TensorFlow Lite (TFL) v2.7.0, which does not support arm64 simulators. Support was added in v2.9.1.

To address this limitation, we have prepared a custom TensorFlowLiteC framework which combines different the architectures, to make it possible to use the same TensorFlowLiteC framework on devices and simulators. The xcframework file is composed of:

* TFL framework v2.7.0 for arm64 iphoneos.
* TFL framework v2.9.1 for x86\_64 iphonesimulator.
* TFL framework v2.9.1 for arm64 iphonesimulator.

You can find the xcframework in [our repository](https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC-2.7.0.tar.gz), along with the [podspec file](https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC.podspec). This custom TFL framework is also bundled in our fat framework and xcframework artifacts.

To make use of it with CocoaPods, you can add the following to your Podfile:

```ruby
pod 'TensorFlowLiteC', :podspec => 'https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC.podspec'
```

This will replace the TFL framework referenced from CocoaPods with our custom one.

At the moment, this framework allows you to build and run your Sentiance integrated app on an M1 simulator, however the SDK is not yet fully compatible with TFL v2.9.1, and will therefore not produce meaningful results.
