# Manual Installation

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Including the SDK

## Step 1

#### Download Sentiance iOS SDK:

| [Sentiance iOS SDK 5.15.0 Framework](https://sentiance-u1-sdk-downloads.s3-eu-west-1.amazonaws.com/ios/frameworks/SENTSDK-5.15.0.framework.zip) |
| ----------------------------------------------------------------------------------------------------------------------------------------------- |

| [Sentiance iOS SDK 5.15.0 XCFramework](https://sentiance-u1-sdk-downloads.s3-eu-west-1.amazonaws.com/ios/frameworks/SENTSDK-5.15.0.xcframework.zip) |
| --------------------------------------------------------------------------------------------------------------------------------------------------- |

## Step 2

#### After you've downloaded and unzipped the SDK, import it as a linked library in your Xcode project:

1. Go to the **General** tab of your target settings
2. Click the **+** button under the **Frameworks, Libraries, and Embedded Content** heading
3. Click **Add Other** and then **Add Files**
4. Choose the **Sentiance XCFramework** file and click **Open**
5. After the item has been added to the list, change the **Embed** option next to the framework to **Do Not Embed**
6. Depending on your Xcode setup, it might be required to add the following libraries: **libz.tbd (previously libz.dylib), CoreMotion, SystemConfiguration, CoreLocation, Foundation, CallKit, CoreTelephony, CoreData**

## Step 3

#### Include the SDK bundle in your project:

1. Go to the **Build Phases** tab of your target settings
2. Expand the **Copy Bundle Resources** row and click the **+** button
3. Choose the **SENTSDK.bundle** file located inside **SENTSDK library**

## **Step 4**

#### Include the TensorFlowLiteC library in your project

1. Go to the **General** tab of your target settings
2. Click the **+** button under the **Frameworks, Libraries, and Embedded Content** heading
3. Click **Add Other** and then **Add Files**
4. Go to the **Frameworks** folder inside the Sentiance framework, select **TensorFlowLiteC.xcframework** and click **Open**
5. After the item has been added to the list, change the **Embed** option next to the framework to **Do Not Embed**

## Step 5

#### Build Settings

1. Go to the **Build Settings** tab of your target settings
2. Look for **Other Linker Flags** in the **Linking** section
3. Add `-lz`, `-all_load` and `-lc++`

![](<../../../../.gitbook/assets/Screen Shot 2020-05-05 at 3.41.04 PM.png>)
