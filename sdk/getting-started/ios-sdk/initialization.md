# 6. Initialization

{% hint style="info" %}
Until the SDK is properly initialized, none of the methods in the SDK will work, with the exception of `sharedInstance`, `initWithConfig` and `getInitState.`
{% endhint %}

In the project's AppDelegate file,

```objectivec
@import SENTSDK;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Creation of SENTConfig here, see previous step
   SENTConfig *conf = [[SENTConfig alloc] initWithAppId:@"APPID"
                                           secret:@"SECRET"
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

