# 5. Configuration

In the `didFinishLaunchingWithOptions` method of your `AppDelegate`, create a `SENTConfig` object with your Sentiance app ID and secret.

```text
@import SENTSDK;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    SENTConfig *conf = [[SENTConfig alloc] initWithAppId:@"APPID"
                                           secret:@"SECRET"
                                           launchOptions:launchOptions];
}
```

If you don't have an app ID and secret yet, read [these instructions](../#create-an-application).

## Optional: SDK Status update handler

This is optional, but indispensable if you want to be kept up-to-date of changes to the SDK status.

```text
[conf setDidReceiveSdkStatusUpdate:^(SENTSDKStatus *status) {
}];
```

For more information related to the `SENTSDKStatus` class, see [this guide](https://developers.sentiance.com/docs/sdk/ios/status).

