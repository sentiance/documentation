# Detecting Vehicle Crashes

The Sentiance SDK can be configured to detect vehicle accidents/crashes during trips. You can be notified of these crash events by setting a handler as follows:

{% tabs %}
{% tab title="iOS" %}
```swift
Sentiance.shared.setVehicleCrashHandler { crashEvent in
    // Handle event
}
```
{% endtab %}

{% tab title="Android" %}
```kotlin
CrashDetectionApi.getInstance(context).setVehicleCrashListener { vehicleCrashEvent ->

}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
To access the [`CrashDetectionApi`](../api-reference/android/crashdetectionapi.md) class on Android, you need to add a dependency on the **com.sentiance:sdk-crash-detection** artifact in your app's _build.gradle_ file.
{% endhint %}
