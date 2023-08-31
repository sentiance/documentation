# Bundle format unrecognized, invalid, or unsuitable

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

If you see an error similar to this:

```text
.../Frameworks/SENTSDK.framework: bundle format unrecognized, invalid, or unsuitableCommand 
CodeSign failed with a nonzero exit code
```

Please follow the steps below:

1. Go to Xcode menu bar and select **File &gt; Project Settings \(or Workspace Settings\)**.
2. Under **Per-User Workspace Settings**, find the shortcut to **DerivedData** folder and open it via Finder.
3. Remove the entire content of the folder and empty the Trash.
4. Restart Xcode.
5. Select the workspace \(or xcodeproj\) file in Xcode project navigator.
6. Select your target and then **Build Phases**.
7. Under **Link Binary with Libraries**, select “+” and add the SENTSDK.framework file to the list.
8. Go to the **General** tab and make sure “SENTSDK.framework” is added with the **Do Not Embed** option.

Some Xcode projects with certain configuration combinations might require these additional steps below to successfully fix the issue:

1. Go to Xcode menu bar and select **File &gt; Project Settings \(or Workspace Settings\)**.
2. Go to **Shared Workspace Settings** &gt; **Build System** and switch to **Legacy Build System**.
3. Go to **Per-User Workspace Settings &gt; Build System** and switch to **Legacy Build System**.

