# M1 Simulator Support

It's possible to build your Sentiance integrated app for the M1 Mac Simulator.

The SDK framework includes support for the arm64 simulator architecture, which is the target architecture for the M1 Mac simulator. However, the SDK has a dependency on TensorFlow Lite (TFL) v2.7.0, which does not support arm64 simulators. Support was added in v2.9.1.

To address this limitation, we have prepared a custom TensorFlowLiteC framework which combines different the architectures, to make it possible to use the same TensorFlowLiteC framework on devices and simulators. The XCFramework file is composed of:

* TFL frameworks v2.7.0 for armv7 and arm64, for iphoneos.
* TFL frameworks v2.9.1 for x86\_64 and arm64, for iphonesimulator.

You can find the XCFramework in [our repository](https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/SENTTensorFlowLiteC.xcframework.zip), along with the [podspec file](https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC.podspec). This custom TFL framework is also bundled in our umbrella framework and XCFramework artifacts.

To use it with CocoaPods, you can add the following to your Podfile:

```ruby
pod 'TensorFlowLiteC', :podspec => 'https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC.podspec'
```

This will replace the TFL framework referenced from CocoaPods with the custom one.

At the moment, this framework allows you to build and run your Sentiance integrated app on an M1 simulator, however the SDK is not yet fully compatible with TFL v2.9.1, and will therefore not produce meaningful results.
