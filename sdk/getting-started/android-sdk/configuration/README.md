# 2. Configuration

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

To initialize the Sentiance SDK, you first need to prepare a configuration object of type [`SdkConfig`](../../../api-reference/android/sdkconfig/) that includes your Sentiance appID and secret key. Head over to the [apps section](https://developers.sentiance.com/apps) of your developer account to grab these.

Depending on your app's configuration and OS version, the SDK may need to start a foreground service every now and again. You must therefore pass a notification that can be used by the service. In the next section, you'll find a handy notification creation method.

{% hint style="info" %}
Please read our [notification management](../../../appendix/android/notification-management.md) section to learn how to build user friendly notifications.
{% endhint %}

Create an [`SdkConig`](../../../api-reference/android/sdkconfig/) object as follow:

```java
SdkConfig config = new SdkConfig.Builder(APP_ID, SECRET, notification)
                                .setMetaUserLinker(userLinker)
                                .build();
```

{% hint style="danger" %}
In the above example, we hard-code the the appID and secret key for testing purposes. However, this is not secure and can lead to leaked credentials. In your own app, load these credentials from a secure source such a remote server, and store them securely on the device.
{% endhint %}

The `SdkConfig` accepts a `userLinker` which is responsible for handling [user linking](../../../../important-topics/user-linking-2.0.md). The linker is invoked by the SDK when creating a Sentiance user \(during the first initialization\) to give you a chance to link your app's user to the Sentiance user. If linking succeeds, this linker does not get invoked during subsequent SDK intializations, unless [the SDK gets reset](../../../api-reference/android/sentiance.md#reset).

```java
MetaUserLinker userLinker = new MetaUserLinker() {
    @Override
    public boolean link(String installId) {
        // Supply the 'installId' to your server, which should then initiate
        // a user linking request with the Sentiance backend.
        
        return requestLinking(installId); // return true if user linking succeeds
    }
};
```

The above implementation expects synchronous execution. Alternatively, you can use [`MetaUserLinkerAsync`](../../../api-reference/android/metauserlinkerasync.md) which is the async variant of the linker. You then notify the SDK about the linking result by calling [`onSuccess()`](../../../api-reference/android/metauserlinkercallback.md#onsuccess) or [`onFailure()`](../../../api-reference/android/metauserlinkercallback.md#onfailure).

You can learn more about user linking [here](../../../../important-topics/user-linking-2.0.md). To see what other SDK configuration options are available, see [`SdkConfig.Builder`](../../../api-reference/android/sdkconfig/sdkconfig-builder.md).

