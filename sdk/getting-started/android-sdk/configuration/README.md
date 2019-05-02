# 2. Configuration

To initialize the Sentiance SDK, you first need to prepare a configuration object of type [`SdkConfig`](../../../api-reference/android/sdkconfig/) that includes your Sentiance appID and secret key. Head over to the [apps section](https://developers.sentiance.com/apps) of your developer account to grab these.

Depending on your app's configuration and OS version, the SDK may need to start a foreground service every now and again. You must therefore pass a notification that can be used by the service. In the next section, you'll find a handy notification creation method.

{% hint style="info" %}
Please read our [notification management](../../../appendix/android/notification-management.md) section to learn how to build user friendly notifications.
{% endhint %}

Create an [`SdkConig`](../../../api-reference/android/sdkconfig/) object as follow:

```java
SdkConfig config = new SdkConfig.Builder(APP_ID, SECRET, notification).build();
```

{% hint style="danger" %}
In the above example, we hard-code the the appID and secret key for testing purposes. However, this is not secure and can lead to leaked credentials. In your own app, load these credentials from a secure source such a remote server, and store them securely on the device.
{% endhint %}

To learn more about the SDK configuration options, see [`SdkConfig.Builder`](../../../api-reference/android/sdkconfig/sdkconfig-builder.md).

