# Using Swift Package Manager

[Swift Package Manager](https://developer.apple.com/documentation/xcode/swift-packages) is a dependency manager for Objective-C and Swift, which simplifies adding 3rd-party frameworks to your projects. See the [Adding Package Dependencies](https://developer.apple.com/documentation/xcode/adding-package-dependencies-to-your-app) page on the Apple developer docs for more details.

## Steps

1. In your Xcode project, go to File -> Add Packages.
2. In the search bar, enter the URL below:

```html
https://github.com/sentiance/sentsdk-package
```

1. Select **sentsdk-package** from the results.
2. Choose "Up to Next Minor Version" as the Dependency Rule, and enter the target SDK version.
3. Select your project from the "Add to Project" section, and click Add Package. Wait for the product selection dialog to load.
4. From the dialog, select **SENTSDK**, and optionally the other products (see next section).
5. Finally in your project build settings, add the following to the **Other Linker Flags**: `-lz`, `-lc++`, and `-all_load`.

## Swift Package Products

The Swift Package defines some Sentiance SDK dependencies as individual products. These include:

* **UnzipKit**: the [UnizipKit](https://github.com/abbeycode/UnzipKit) code, packaged as an XCFramework.
* **ProtocolBuffersObjC**: the [ProtocolBuffers Obj-C](https://github.com/protocolbuffers/protobuf/tree/main/objectivec) code, packaged as an XCFramework.
* **TensorFlowLiteC**: Sentiance's [custom](../../../appendix/ios/m1-simulator-support.md) TensorFlowLiteC XCFramework, supporting M1 simulators.

These dependencies must be met in order for your app to build successfully. If your app already includes a [compatible version](../../../appendix/ios/dependencies.md) of a dependency, you can omit it when adding the Sentiance SDK package.

