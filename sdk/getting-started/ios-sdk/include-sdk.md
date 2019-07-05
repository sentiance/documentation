---
description: We offer two SDK integration options. Podfile and manual.
---

# 1. Including the SDK

## Manual

Download Sentiance iOS SDK: [Sentiance iOS SDK 5.4.0](https://sentiance-sdk.s3-eu-west-1.amazonaws.com/ios/transport/SENTSDK-5.4.0.framework.zip)

After you've downloaded and unzipped the SDK, import it as a linked framework in your Xcode project:

1. Go to the **General** tab of your target settings
2. Click the **+** button under the **Linked Frameworks and Libraries** heading
3. Click **Add Other**
4. Choose the Sentiance framework file and click **Open**
5. Depending on your Xcode setup, it might be required to add the following libraries: **libz.tbd \(previously libz.dylib\), CoreMotion, SystemConfiguration, CoreLocation, Foundation, CallKit, CoreTelephony, CoreData**

You'll also need to include the SDK bundle in your project:

1. Go to the **Build Phases** tab of your target settings
2. Expand the **Copy Bundle Resources** row and click the **+** button
3. Choose the **SENTSDK.bundle** file located inside **SENTSDK.framework**

