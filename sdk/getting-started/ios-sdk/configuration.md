# 3. Usage

In the `didFinishLaunchingWithOptions` method of your `AppDelegate`, create a [`SENTConfig`](../../api-reference/ios/sentconfig-1.md) object with your Sentiance app ID and secret.

```objectivec
@import SENTSDK;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    SENTConfig *conf = [[SENTConfig alloc] initWithAppId:@"APPID"
                                           secret:@"SECRET"
                                           link:userLinker
                                           launchOptions:launchOptions];
}
```

If you don't have an appID and secret key yet, read [these instructions](../#create-an-application).

{% hint style="danger" %}
In the above example, we hard-code the the appID and secret key for testing purposes. However, this is not secure and can lead to leaked credentials. In your own app, load these credentials from a secure source such a remote server, and store them securely on the device.
{% endhint %}

`SENTConfig` accepts a `userLinker` which is responsible for handling [user linking](../../../important-topics/user-linking-2.0.md). The linker is invoked by the SDK when creating a Sentiance user \(during the first initialization\) to give you a chance to link your app's user to the Sentiance user. If linking succeeds, this linker does not get invoked during subsequent SDK intializations, unless [the SDK gets reset](../../api-reference/ios/sentsdk/#reset-failure).

```objectivec
MetaUserLinker userLinker = ^(NSString *installId, void (^linkSuccess)(void), void (^linkFailed)(void)) {
    // Supply the 'installId' to your server, which should then initiate
    // a user linking request with the Sentiance backend.
    
    [self requestLinking:installId completion:^(BOOL success) {
        if (success) {
            linkSuccess(); // Call if linking succeeds
        } else {
            linkFailed();  // Call if linking fails
        }
    }];
};
```

You can learn more about user linking [here](../../../important-topics/user-linking-2.0.md).

## Optional: SDK Status update handler

This step is optional, but indispensable if you want to be kept up-to-date with changes to the [SDK status](../../api-reference/ios/sentsdk/sentsdkstatus.md).

```text
[conf setDidReceiveSdkStatusUpdate:^(SENTSDKStatus *status) {
}];
```

For more information related to the [`SENTSDKStatus`](../../api-reference/ios/sentsdk/sentsdkstatus.md) class, see [this guide](https://developers.sentiance.com/docs/sdk/ios/status).

## Initializing the SDK

{% hint style="info" %}
Until the SDK is properly initialized, none of the methods in the SDK will work, with the exception of `sharedInstance`, `initWithConfig` and `getInitState.`
{% endhint %}

In the project's `AppDelegate` file,

```objectivec
@import SENTSDK;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Creation of SENTConfig here, see previous step
   SENTConfig *conf = [[SENTConfig alloc] initWithAppId:@"APPID"
                                           secret:@"SECRET"
                                           link:userLinker
                                           launchOptions:launchOptions];
   
   // Initialize SDK
    [[SENTSDK sharedInstance] initWithConfig:conf success:^{

    } failure:^(SENTInitIssue issue) {

    }];

    return YES;
}
```

1. In the `didFinishLaunchingWithOptions` method of your `AppDelegate`, pass the [`SENTConfig`](../../api-reference/ios/sentconfig-1.md) you created in the previous step to the `initWithConfig` method of the Sentiance SDK.
2. Additionally, [`success`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure) and [`failure`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure) blocks must be passed as well, which will inform you when initialization has succeeded or failed.

{% hint style="warning" %}
The [`initWithConfig:`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure)call must be executed before `didFinishLaunchingWithOptions:` returns. Therefore, you must call it synchronously on the main UI thread. If you plan to add a remote flag to control the initialization \(e.g. Firebase Remote Config\), make sure the check is synchronous \(e.g. using a cached flag\).

See [here](../../appendix/sdk-initialization.md#why-initialize-in-the-application-appdelegate-class) to understand more about why this is important.
{% endhint %}



## Starting Detections

We recommend that SDK startup is done within `didFinishLaunchingWithOptions` of `AppDelegate` file to ensure that there are no unintended side effects.

Call the `start` method from the `success` block of the [`initWithConfig`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure) method:

```objectivec
[[SENTSDK sharedInstance] start:^(SENTSDKStatus *status) {
    if ([status startStatus] == SENTStartStatusStarted) {
        // SDK started properly.
    } else if ([status startStatus] == SENTStartStatusPending) {
        // Something prevented the SDK to start properly (check the location permission). Once fixed, the SDK will start automatically.
    } else {
        // SDK did not start.
    }
}];
```

You can check the `status` to see whether starting has succeeded correctly or not.

## Overall Code

```objectivec
@import SENTSDK;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Creation of SENTConfig here, see previous step
   SENTConfig *conf = [[SENTConfig alloc] initWithAppId:@"APPID"
                                           secret:@"SECRET"
                                           link:userLinker
                                           launchOptions:launchOptions];
   
   // Initialize SDK
    [[SENTSDK sharedInstance] initWithConfig:conf success:^{

        // SDK Start
       [[SENTSDK sharedInstance] start:^(SENTSDKStatus *status) {
            if ([status startStatus] == SENTStartStatusStarted) {
                // SDK started properly.
            } else if ([status startStatus] == SENTStartStatusPending) {
                // Something prevented the SDK to start properly (check the location permission). Once fixed, the SDK will start automatically.
            } else {
            // SDK did not start.
            }
        }];

    } failure:^(SENTInitIssue issue) {

    }];

    return YES;
}
```

