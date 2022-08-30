# Dependencies

This page lists the dependencies of the Sentiance iOS SDK. These dependencies are bundled as XCFramework packages within the umbrella SDK XCframework, which you can utilize when doing a manual integration. For CocoaPods and Swift Package Manager integrations, they are added as external or additional dependences.

* TensorFlowLiteC: v2.7.0
* ProtocolBuffers (ObjectiveC): v3.18
* UnzipKit: v1.9

Apart from the above, all variants of the Sentiance SDK XCFramework include _mpde.xcframework_ under the framework's _External_ directory_,_ which must always be added to your project during manual integrations.
