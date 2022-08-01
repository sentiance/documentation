# 3. Initialization

Initialization sets up internal SDK components to allow the creation of a Sentiance user on the device, and perform detections in the background.&#x20;

Only a limited set of SDK functions are allowed to be invoked before initializing the SDK.

### iOS

The correct way to natively initialize on iOS is to do it inside the `application:didFinishLaunchingWithOptions:` method of the `AppDelegate` class.

{% code title="AppDelegate.m" %}
```swift
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    SENTInitializationResult *result = [[[RNSentianceHelper alloc] init] initializeSDKWithLaunchOptions:launchOptions];
    return YES;
}
```
{% endcode %}

Initialization will normally succeed, unless an unexpected error or exception is encountered. In case of failure, you can check the reason via the returned result.

```swift
if (result.isSuccessful) {
    NSLog(@"Initialization succeeded");
}
else {
    NSLog(@"Initialization failed with reason %lu", result.failureReason);
}
```

### Android

Add the following code inside the `onCreate()` method of your `Application` class:

```java
...
import com.sentiance.sdk.init.InitializationResult;
import com.sentiance.react.bridge.core.SentianceHelper;

public class MainApplication extends Application implements ReactApplication {

    @Override
    public void onCreate() {
        super.onCreate();
        ...
        
        SentianceHelper sentianceHelper = SentianceHelper.getInstance(this);
        InitializationResult result = sentiancehelper.initializeSDK();
    }

  ...
}
```

Initialization will normally succeed, unless an unexpected error or exception is encountered. In case of failure, you can check the reason via the returned result.

```java
if (result.isSuccessful()) {
    Log.d(TAG, "Initialization succeeded");
} else {
    Log.e(TAG, "Initialization failed with reason " + result.getFailureReason().getName(), result.getThrowable());
}
```

To learn more about Initialization, see the [SDK Initialization](../../appendix/sdk-initialization.md) page.
