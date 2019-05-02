# SENTConfig

The SENTConfig class allows you to specify your Sentiance app ID and secret when initializing the Sentiance SDK.

### Enable Triggered Trips

Triggered trips enables controlled detections from your app. To run the SDK in triggered trips mode, use the following configuration option:

```objectivec
[config setIsTriggeredTrip: TRUE];
```

Learn more about triggered trips [here](../../appendix/controlled-detections/controlled-trips-only.md).

### Meta-User Linking

Sentiance assigns to each user a unique ID. You can link your app's user to the Sentiance user using meta-user linking. The linking step involves server-to-server communication, and is triggered by the SDK via a meta-user linking callback. You can implement this callback method as follows:

```objectivec
MetaUserLinker metaUserlink = ^(NSString *installId, 
                                void (^linkSuccess)(void), 
                                void (^linkFailed)(void)) { }

SENTConfig *config = [[SENTConfig alloc] initWithAppId:APPID
                                                secret:SECRET
                                                  link:metaUserlink
                                         launchOptions:launchOptions];
```

Learn more about meta-users [here](../../appendix/user-linking.md).

## SENTConfig API:

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

Key value pair passed from \[AppDelegate application:application didFinishLaunchingWithOptions:launchOptions\]

```objectivec
@property (nonatomic, strong) NSDictionary *launchOptions;
```

### didReceiveSdkStatusUpdate

Callback to receive current status of SDK. Returns [SENTSDKStatus]()

```objectivec
@property (nonatomic, copy) void (^didReceiveSdkStatusUpdate)(SENTSDKStatus* issue);
```

### link

[MetaUserLinker](../android/metauserlinker.md) linking handler your own user to a Sentiance user.

```objectivec
@property (nonatomic, copy) MetaUserLinker link;
```

### initWithAppId: secret: launchOptions:

SDK configuration initialization method. Returned SENTConfig object is passed to \[SENTSDK initWithConfig\].

```objectivec
- (id)initWithAppId: (NSString *) appId 
             secret: (NSString *) secret 
      launchOptions: (NSDictionary *) launchOptions;
```

| Parameter |  |
| :--- | :--- |
| appId | Application key which you get from Sentiance account. |
| secret | Secret key which you get from Sentiance account. |
| launchOptions | A dictionary indicating the reason the app was launched \(if any\). The contents of this dictionary may be empty in situations where the user launched the app directly. For information about the possible keys in this dictionary and how to handle them, see [Launch Options Keys](https://developer.apple.com/documentation/uikit/uiapplicationlaunchoptionskey?language=objc). |

### initWithAppId: secret: link: launchOptions:

SDK config intialization method with linking to customer's user id. It creates a continuous Sentiance profile across application installations and re-installations on different devices, linked together by their own user id.

```objectivec
- (id)initWithAppId: (NSString *) appId 
             secret: (NSString *) secret 
               link: (MetaUserLinker) link 
      launchOptions :(NSDictionary *) launchOptions;
```

| Parameter |  |
| :--- | :--- |
| appId | Application key which you get from Sentiance account. |
| secret | Secret key which you get from Sentiance account. |
| link | [MetaUsersLinker](../android/metauserlinker.md) type block which returns linkSuccess or linkFailed depended on how linking gone. Use InstallId to link with backend. |
| launchOptions | A dictionary indicating the reason the app was launched \(if any\). The contents of this dictionary may be empty in situations where the user launched the app directly. For information about the possible keys in this dictionary and how to handle them, see [Launch Options Keys](https://developer.apple.com/documentation/uikit/uiapplicationlaunchoptionskey?language=objc). |

### isValidConfig

Check if App ID and Secret are valid

```objectivec
- (BOOL)isValidConfig
```

