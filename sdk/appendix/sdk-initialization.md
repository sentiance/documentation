# SDK Initialization

## What Does Initialization Do?

During initialization, the Sentiance SDK will construct all the components necessary to do detections, networking, and maintenance work.

The first time the SDK is initialized, a unique ID will be assigned to the device. All detections made on this device will be tagged with this ID as they get uploaded to the server to create a user timeline. Additionally, a configuration will be loaded from the server to determine detection parameters like location request intervals, sensors to record, and sampling rates. Last but not least, the SDK will schedule jobs and alarms for purposes of uploading data to the server and performing internal maintenance.

Subsequent initializations will ensure the SDK components are constructed and ready to handle incoming broadcast intents and alarms.

## Why Initialize in the Application / AppDelegate Class?

Once the Sentiance SDK has been initialized, it will set jobs, alarms, and geofences as part of the detection process. When your app is not running and a geofence event occurs, the system will start the process and deliver the broadcast intent or notification directly to the SDK. Therefore, the SDK must already be initialized before handling this event.

Initializing the SDK in the `onCreate()` or `didFinishLaunchingWithOptions` method of your `Application` / `AppDelegate` class will ensure the SDK components are constructed, since these methods are guaranteed to finish before an intent or a notification is delivered to any broadcast receiver / delegate function.

{% hint style="info" %}
The only exception to the above rule is the first ever SDK initialization call. This can be delayed since the SDK has not yet set any alarms, geofences, etc. A good reason to delay this first call for example, is when you need to download the Sentiance credentials from a remote server, or you need to handle a first user login.
{% endhint %}

Another important consideration is that when initializing inside `onCreate()` and `didFinishLaunchingWithOptions`, it **must be done synchronously on the main application \(UI\) thread**. When `onCreate()` or `didFinishLaunchingWithOptions` is finished, `init` should have already returned. Therefore, using `DispatchQueue.main.async` or `Handler.post(Runnable)` is not permitted.

{% hint style="info" %}
On Android, when the SDK detects improper initialization, it will output the following error to logcat: "**SDK is not initialized. Make sure to call Sentiance.init\(\) in your Application.onCreate\(\) method.**"
{% endhint %}

## Initialization Must be Done Only Once

You should only ever call [`init()`](../api-reference/android/sentiance.md#init) or `initWithConfig` if the SDK has not been initialized. Calling these methods more than once will throw an [`SdkException`](../api-reference/android/sdkexception.md) or `NSException`. This is intentional to guarantee single execution of the  logic you've implement in the success method of your initialization callback.

To check whether the SDK has been initialized, call `getInitState`. This will return one of the following enums:

{% tabs %}
{% tab title="iOS" %}
* `SENTInitialized`
* `SENTNotInitialized`
* `SENTInitInProgress`
{% endtab %}

{% tab title="Android" %}
* `INITIALIZED`
* `NOT_INITIALIZED`
* `INIT_IN_PROGRESS`
{% endtab %}
{% endtabs %}

