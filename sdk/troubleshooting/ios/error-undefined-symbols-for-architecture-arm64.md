# Error: Undefined symbols for architecture arm64

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

If you see error similar to this:

```objectivec
"Undefined symbols for architecture arm64:
  "OBJC_CLASS$_CXCallObserver", referenced from:
      objc-class-ref in SENTSDK(SENTCallHandler.o)
ld: symbol(s) not found for architecture arm64 "
```

It means that framework is not included. Please check [step 1 in the iOS Quick start](../../getting-started/ios-sdk/1.-installation/manual-installation.md) or simply:

1. Go to your **Project**
2. Select your **Target**
3. Go to **Build Phases**
4. Open **Link Binary With Libraries**
5. Press **+** to Add the **SENTSDK.framework** (use **Add Other** button if needed)

