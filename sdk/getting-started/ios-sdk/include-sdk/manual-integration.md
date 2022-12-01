# Manual Integration

### 1. Download the SDK

Download the latest Sentiance iOS SDK [v6.1.3](https://sentiance-u1-sdk-downloads.s3-eu-west-1.amazonaws.com/ios/frameworks/SENTSDK/6.1.0/SENTSDK-6.1.3.xcframework.zip).

### 2. Import the Framework <a href="#manual-integration-step-2" id="manual-integration-step-2"></a>

After you've downloaded and unzipped the SDK, import it as a linked library in your Xcode project:

1. Go to the **General** tab of your target settings.
2. Click the **+** button under the **Frameworks, Libraries, and Embedded Content** heading.
3. Click **Add Other** and then **Add Files**.
4. Choose the **Sentiance XCFramework** file and click **Open**.
5. After the item has been added to the list, change the **Embed** option next to the framework to **Do Not Embed**.
6. Depending on your Xcode setup, it might be required to add the following libraries: libz.tbd (previously libz.dylib), CoreMotion, SystemConfiguration, CoreLocation, Foundation, CallKit, CoreTelephony, CoreData.

### 3. Include the SDK Bundle <a href="#manual-integration-step-3" id="manual-integration-step-3"></a>

Include the SDK bundle in your project:

1. Go to the **Build Phases** tab of your target settings.
2. Expand the **Copy Bundle Resources** row and click the **+** button.
3. Choose the **SENTSDK.bundle** file located inside **SENTSDK library**.

### **4. Import the Dependencies**

The SDK XCFramework bundles all its necessary dependencies under the **External** directory. For each dependency, do the following:

1. Go to the **General** tab of your target settings.
2. Click the **+** button under the **Frameworks, Libraries, and Embedded Content** heading.
3. Click **Add Other** and then **Add Files**.
4. Go to the **Frameworks** folder inside the Sentiance framework, select the dependency .**xcframework** file and click **Open**.
5. After the item has been added to the list, update the **Embed** option next to the framework as follows:

| Framework                       | Embed Option |
| ------------------------------- | ------------ |
| ProtocolBuffers.xcframework     | Do Not Embed |
| UnzipKit.xcframework            | Do Not Embed |
| SENTTensorFlowLiteC.xcframework | Embed & Sign |
| mpde.xcframework                | Embed & Sign |

To learn more about these dependencies, see [this page](../../../appendix/ios/dependencies.md).

### 5. Update the Build Settings

1. Go to the **Build Settings** tab of your target settings.
2. Look for **Other Linker Flags** in the **Linking** section.
3. Add `-lz` , `-all_load`, and `-lc++`
