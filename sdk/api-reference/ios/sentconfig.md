# SENTConfig

The `SENTConfig` class allows you to specify your Sentiance app ID and secret when initializing the Sentiance SDK. Moreover, it allows you to set additional options and callbacks.

## // todo: change to api doc format.

## Enable Triggered Trips

Triggered trips enables controlled detections from your app. To run the SDK in triggered trips mode, use the following configuration option:

```objectivec
[config setIsTriggeredTrip: TRUE];
```

Learn more about triggered trips [here](../../appendix/controlled-detections/controlled-trips-only.md).

## SENTSDKStatus Handler

At runtime, the SDK will occasionally send status updates to your app. These are concerning the detection status and environment changes \(e.g. device configuration changes, etc.\). You can set the status updates handler on the `SENTConfig` object as follows:

```objectivec
[conf setDidReceiveSdkStatusUpdate:^(SENTSDKStatus *status) { }];
```

Learn more about handling `SdkStatus` updates [here]().

## Meta-User Linking

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

Learn more about meta-users [here](../../appendix/meta-users.md).

