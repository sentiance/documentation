# Dependencies

This page lists the dependencies of the Sentiance iOS SDK. These dependencies are bundled as xcframework packages within the "fat" SDK xcframework, which you can utilize when doing a manual integration. For CocoaPods integrations, they are added as CocoaPods dependences.

* TensorFlow Lite: v2.7.0
* Protobuf: v3.18
* UnzipKit: v1.9

Apart from the above, both regular and "thin" versions of the Sentiance SDK include _mpde.xcframework_ under the framework's _External_ directory_,_ which must always be added to your project (done automatically for CocoaPods integrations).
