# 7. Starting Detections

We recommend that SDK startup is done within `didFinishLaunchingWithOptions` of `AppDelegate` file to ensure that there are no unintended side effects.

Call the `start` method from the `success` block of the [`initWithConfig`](../../api-reference/ios/sentsdk/#initwithconfig-success-failure) method:

```text
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

Overall Code:

```objectivec
@import SENTSDK;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Creation of SENTConfig here, see previous step
   SENTConfig *conf = [[SENTConfig alloc] initWithAppId:@"APPID"
                                           secret:@"SECRET"
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



