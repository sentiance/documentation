---
description: Wrapper class of options while Initializing the SDK
---

# SENTOptions

### platformURL

The Sentiance platform URL. Use this only if you are migrating from an older SDK version (5.x)

```objectivec
@property (nonatomic, copy, nullable) NSString *platformUrl;
```



### isAppSessionDataCollectionAllowed

Informs whether app session data collection is enabled.

If enabled, the SDK may collect additional sensor and location data when the app is in the foreground (i.e visible to the user). This data may get uploaded to the Sentiance Platform.

```objectivec
@property (nonatomic) BOOL isAppSessionDataCollectionAllowed;
```



### registerBackgroundTaskIdentifiers

Set to NO to prevent the SDK from registering its own background task identifiers during initialization.

By default, this is set to YES. You should set it to NO only when initializing the SDK outside of your app delegate’s `application:didFinishLaunchingWithOptions:launchOptions:` method, as registering tasks outside of this method can cause iOS to terminate your app.
