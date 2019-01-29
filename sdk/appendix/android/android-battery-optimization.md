# Android Battery Optimization

When running the SDK on Android 6 and higher, it is recommended to ask the user to disable battery optimization for your app. This makes sure that SDK detections continue to work properly when the device is in Doze mode. Moreover, on Android Pie, it will prevent Adaptive Battery from [bucketing](https://developer.android.com/about/versions/pie/power#buckets) your app based on usage and [restricting background processing](https://developer.android.com/reference/android/app/ActivityManager#isBackgroundRestricted%28%29), all of which that can impact the detection quality of the SDK.

After explaining to the user about the benefits of disabling battery optimization, call the [`disableBatteryOptimization()`](../../api-reference/android/sentiance.md#disablebatteryoptimization) method of the [`Sentiance`](../../api-reference/android/sentiance.md) class. This will trigger a system dialog asking the user to allow disabling battery optimization for your app.

```java
Sentiance.getInstance(context).disableBatteryOptimization();
```

The Sentiance SDK does not define the `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` permission required for this feature. You must therefore explicitly add this permission to your app.

{% code-tabs %}
{% code-tabs-item title="AndroidManifest.xml" %}
```markup
<uses-permission 
	android:name="android.permission.REQUEST_IGNORE_BATTERY_OPTIMIZATIONS"/>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="danger" %}
Please note that Google Play policies prohibit apps from requesting this permission unless the app's core functionality is affected. For more information about the supported use cases, see [here](https://developer.android.com/training/monitoring-device-state/doze-standby#whitelisting-cases).
{% endhint %}



