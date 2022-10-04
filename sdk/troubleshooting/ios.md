# iOS

## Bundle format unrecognized, invalid, or unsuitable

If you see an error similar to this:

```
.../Frameworks/SENTSDK.framework: bundle format unrecognized, invalid, or unsuitableCommand 
CodeSign failed with a nonzero exit code
```

Please follow the steps below:

1. Go to Xcode menu bar and select **File > Project Settings (or Workspace Settings)**.
2. Under **Per-User Workspace Settings**, find the shortcut to **DerivedData** folder and open it via Finder.
3. Remove the entire content of the folder and empty the Trash.
4. Restart Xcode.
5. Select the workspace (or xcodeproj) file in Xcode project navigator.
6. Select your target and then **Build Phases**.
7. Under **Link Binary with Libraries**, select “+” and add the SENTSDK.framework file to the list.
8. Go to the **General** tab and make sure “SENTSDK.framework” is added with the **Do Not Embed** option.

Some Xcode projects with certain configuration combinations might require these additional steps below to successfully fix the issue:

1. Go to Xcode menu bar and select **File > Project Settings (or Workspace Settings)**.
2. Go to **Shared Workspace Settings** > **Build System** and switch to **Legacy Build System**.
3. Go to **Per-User Workspace Settings > Build System** and switch to **Legacy Build System**.

## Error: Undefined symbols for architecture arm64

If you see an error similar to this:

```objectivec
"Undefined symbols for architecture arm64:
  "OBJC_CLASS$_CXCallObserver", referenced from:
      objc-class-ref in SENTSDK(SENTCallHandler.o)
ld: symbol(s) not found for architecture arm64 "
```

It means that framework is not included. Please check [step 1 in the iOS Quick start](broken-reference) or simply:

1. Go to your **Project**
2. Select your **Target**
3. Go to **Build Phases**
4. Open **Link Binary With Libraries**
5. Press **+** to Add the **SENTSDK.framework** (use **Add Other** button if needed)

## Bundled model for XXX is incompatible

After updating the Sentiance SDK, if you see an error similar to this:

```
`*** Terminating app due to uncaught exception 'NSInternalInconsistencyException', reason: 'Bundled model for CrashDetector is incompatible'
```

It means your build directory is not clean, and Xcode is merging old and new SDK bundle data. Clean your Xcode DerivedData directory to fix it.
