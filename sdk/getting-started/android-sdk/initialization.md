# 2. Initialization

Initialization sets up internal SDK components to allow the creation of a Sentiance user on the device, and perform detections in the background.&#x20;

Only a limited set of SDK methods are allowed to be invoked before initializing the SDK.

### 1. Create an Application Class

Initialization [must be done](../../appendix/sdk-initialization.md#why-initialize-in-the-application-appdelegate-class) in the `onCreate()` method of your `Application` class. If you don't already have a custom application class, first create a new class that extends `Application`.

{% code title="MyApplication.kt" %}
```kotlin
import android.app.Application;

class MyApplication: Application() {
    override fun onCreate() {
        super.onCreate()
    }
}
```
{% endcode %}

Then reference this new class in the application tag of the `AndroidManifest.xml`

```java
<application android:name="com.example.appname.MyApplication">
  <!-- Activities -->
</application>
```

### 2. Initialize the SDK

In the `onCreate()` method of your `Application` class, call `initialize()`.

{% code title="MyApplication.kt" %}
```kotlin
override fun onCreate() {
    super.onCreate()

    val result = Sentiance.getInstance(this).initialize()
    if (result.isSuccessful) {
        Log.d(TAG, "Initialization succeeded");
    }
}
```
{% endcode %}

Initialization will normally succeed, unless an unexpected error or exception is encountered. In case of failure, you can check the reason via the returned result.

```kotlin
if (result.isSuccessful) {
    Log.d(TAG, "Initialization succeeded");
} else {
    Log.e(TAG, "Intialization failed with reason ${result.failureReason!!.name}", result.throwable);
}
```

<details>

<summary>Custom Notification</summary>

The Sentiance SDK runs independently in the background when detections are enabled. To do so, it makes use of Android Foreground Services. To start a foreground service, the SDK has to pass a Notification to the Android API when foregrounding the service.

You can specify the notification that the SDK should use by passing it to the SDK initializer as an option:

```kotlin
val options = SentianceOptions.Builder(context)
    .setNotification(nofitication, id)
    .build()
Sentiance.getInstance(context).initialize(options)
```

You can find a sample code snippet for creating a notification [here](../../appendix/android/sample-notification.md). Be sure to check our [notification management](../../appendix/android/notification-management.md) page for more on the best practices of using service notifications.

</details>

To learn more about Initialization, see the [SDK Initialization](../../appendix/sdk-initialization.md) page.
