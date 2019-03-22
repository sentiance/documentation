# 6. Initialization

{% hint style="info" %}
Until the SDK is properly initialized, most of the methods in the SDK will not work with the exception of `sharedInstance`, `initWithConfig` and `isInitialized.`
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
2. Additionally, a [`success`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure) and [`failure`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure) block must be passed as well, which will inform you when initialization has failed or succeeded.



