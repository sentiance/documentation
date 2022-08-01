---
description: >-
  The SENTConfig class allows you to specify your Sentiance app ID and secret
  when initializing the Sentiance SDK.
---

# SENTConfig

{% hint style="danger" %}
This class is part of a deprecated Initialization flow. See [here](https://app.gitbook.com/o/-LTy4edtsWdQgbEsKB-i/s/-LTy4edu-AQHCZBbSxqI/\~/changes/-Mdvb7zVAg9mTiQeb82W/sdk/getting-started/ios-sdk/initialization) for the updated initialization steps.
{% endhint %}

## SENTConfig API:

### baseURL

Set the platform base URL

```objectivec
@property (nonatomic, strong) NSString *baseURL;
```

### appId

App ID created and managed by Sentiance's Developer Dashboard

```objectivec
@property (nonatomic, strong) NSString *appId;
```

### secret

Secret token created along with App ID

```objectivec
@property (nonatomic, strong) NSString *secret;
```

### launchOptions

Key value pair passed from \[AppDelegate application:application didFinishLaunchingWithOptions:launchOptions]

```objectivec
@property (nonatomic, strong) NSDictionary *launchOptions;
```

### registerBackgroundTaskIdentifiers

Set to YES to allow the SDK to register its own background task identifiers during initialization.

By default, this is set to NO. You should set it to YES only when initializing the SDK within your app delegate’s `application:didFinishLaunchingWithOptions:launchOptions:` method, as registering tasks outside of this method can cause iOS to terminate your app.

```objectivec
@property (nonatomic, assign) BOOL registerBackgroundTaskIdentifiers;
```

### didReceiveSdkStatusUpdate

Callback to receive current status of SDK. Returns [SENTSDKStatus](sentsdkstatus.md)

```objectivec
@property (nonatomic, copy) void (^didReceiveSdkStatusUpdate)(SENTSDKStatus* issue);
```

### link

[SENTUserLinker](user-creation-and-linking/user-linking/metauserlinker.md) linking handler your own user to a Sentiance user.

```objectivec
@property (nonatomic, copy) SENTUserLinker link;
```

### isTriggeredTrip

Configuration check on trip trigger availability

```objectivec
@property (nonatomic, assign) BOOL isTriggeredTrip;
```

### isValidConfig

```objectivec
- (BOOL)isValidConfig;registerBackgroundTaskIdentifiers
```

Set to **YES** to allow the SDK to register its own background task identifiers during initialization. By default, this is set to **NO**. You should set it to **YES** only when initializing the SDK within your app delegate’s `application:didFinishLaunchingWithOptions:launchOptions:` method, as registering tasks outside of this method can cause iOS to terminate your app.

```objectivec
@property (nonatomic, assign) BOOL registerBackgroundTaskIdentifiers;
```

### isHardEventDetectionEnabled

Check if App ID and Secret are valid

```objectivec
- (BOOL)isValidConfig
```



### User Linking

Sentiance assigns to each user a unique ID. You can link your app's user to the Sentiance user using meta-user linking. The linking step involves server-to-server communication, and is triggered by the SDK via a meta-user linking callback. You can implement this callback method as follows:

```objectivec
SENTUserLinker userlinker = ^(NSString *installId, 
                                void (^linkSuccess)(void), 
                                void (^linkFailed)(void)) { }

SENTConfig *config = [[SENTConfig alloc] initWithAppId:APPID
                                                secret:SECRET
                                                  link:SENTUserLinker
                                         launchOptions:launchOptions];
```

Learn more about UserLinking [here](../../appendix/user-linking.md).



### initWithAppId: secret: launchOptions:

SDK configuration initialization method. Returned SENTConfig object is passed to \[SENTSDK initWithConfig].

```objectivec
- (id)initWithAppId: (NSString *) appId 
             secret: (NSString *) secret 
      launchOptions: (NSDictionary *) launchOptions;
```

| Parameter     |                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| appId         | Application key which you get from Sentiance account.                                                                                                                                                                                                                                                                                                                             |
| secret        | Secret key which you get from Sentiance account.                                                                                                                                                                                                                                                                                                                                  |
| launchOptions | A dictionary indicating the reason the app was launched (if any). The contents of this dictionary may be empty in situations where the user launched the app directly. For information about the possible keys in this dictionary and how to handle them, see [Launch Options Keys](https://developer.apple.com/documentation/uikit/uiapplicationlaunchoptionskey?language=objc). |

### initWithAppId: secret: link: launchOptions:

SDK config intialization method with linking to customer's user id. It creates a continuous Sentiance profile across application installations and re-installations on different devices, linked together by their own user id.

```objectivec
- (id)initWithAppId: (NSString *) appId 
             secret: (NSString *) secret 
               link: (SENTUserLinker) link 
      launchOptions :(NSDictionary *) launchOptions;
```

| Parameter     |                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| appId         | Application key which you get from Sentiance account.                                                                                                                                                                                                                                                                                                                             |
| secret        | Secret key which you get from Sentiance account.                                                                                                                                                                                                                                                                                                                                  |
| link          | SENT[metauserlinker.md](user-creation-and-linking/user-linking/metauserlinker.md "mention")UsersLinker type block which returns linkSuccess or linkFailed depended on how linking gone. Use InstallId to link with backend.                                                                                                                                                       |
| launchOptions | A dictionary indicating the reason the app was launched (if any). The contents of this dictionary may be empty in situations where the user launched the app directly. For information about the possible keys in this dictionary and how to handle them, see [Launch Options Keys](https://developer.apple.com/documentation/uikit/uiapplicationlaunchoptionskey?language=objc). |

###
