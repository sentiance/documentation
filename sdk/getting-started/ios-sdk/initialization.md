---
description: SDK Initialization Steps
---

# 3. Initialization

Initialization sets up internal SDK components to allow the creation of a Sentiance user on the device, and perform detections in the background.&#x20;

Only a limited set of SDK methods are allowed to be invoked before initializing the SDK.

### 1. Initialize in the AppDelegate Class

Initialization [must be done](../../appendix/sdk-initialization.md#why-initialize-in-the-application-appdelegate-class) in the `application:didFinishLaunchingWithOptions:` method of your `AppDelegate` class. If you don't already have a custom AppDelegate set up, first create a new class that extends `Application`.

```swift
class AppDelegate: NSObject, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey : Any]? = nil) -> Bool {   
        return true
    }
}
```

### 2. Import the SDK in your source file.

```objectivec
@import SENTSDK;
```

### 3. Initialize the SDK

In the `application:didFinishLaunchingWithOptions:` method of your `AppDelegate` class, call `initializeWithOptions:launchOptions:`.

{% code title="AppDelegate.swift" %}
```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey : Any]? = nil) -> Bool {   
    let result = Sentiance.shared.initialize(options: SENTOptions(for: .appLaunch))
    if result.isSuccessful {
        NSLog("Initialization succeeded")
    }
    return true
}
```
{% endcode %}

Initialization will normally succeed, unless an unexpected error or exception is encountered. In case of failure, you can check the reason via the returned result.

```swift
if result.isSuccessful {
    NSLog("Initialization succeeded")
} else {
    NSLog("Initialization failed with reason \(result.failureReason)")
}
```

{% hint style="warning" %}
#### Incorrect Initialization

You must initialize the SDK during app startup, before `application:didFinishLaunchingWithOptions:` returns. Therefore, you must do it synchronously on the main thread. If you plan to add a remote flag to control the initialization (e.g. Firebase Remote Config), make sure the check is synchronous (e.g. utilizing a cached flag). See [here](../../appendix/sdk-initialization.md#why-initialize-in-the-application-appdelegate-class) to learn more about why this is important.
{% endhint %}

To learn more about Initialization, see the [SDK Initialization](../../appendix/sdk-initialization.md) page.
