# Android Quick Start

{% hint style="success" %}
### Platform requirements

The Sentiance SDK works on Android 6.0 and above. If you support older Android versions, see [this](../../troubleshooting/android/#manifest-merger-failed-uses-sdk-minsdkversion-x-cannot-be-smaller-than-version-y-declared-in-library) troubleshooting guide.
{% endhint %}

{% hint style="success" %}
### Dependency requirements

#### Google Play Services

The Sentiance SDK uses version 18.0.0 of the Google Play Location service library. This is the minimum required version to ensure optimal SDK detections. If your app depends on a lower version, please be aware that it will be forced to use v18.0.0.

#### TensorFlow Lite

The Sentiance SDK uses version 2.7.0 of the TensorFlow Lite library. If your app depends on a different version, please reach out to Sentiance to address possible incompatibility issues.
{% endhint %}

If you want to get started quickly, you can check out our [sample application](https://github.com/sentiance/sample-apps-android). If you prefer to manually integrate the SDK in your existing app, please read on.
