# User Linking

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

User Linking can be used to connect your app’s user to a Sentiance user in a deeper way.

A user in the Sentiance Platform is identified by a unique **userID**. An SDK instance \(or an app install\) on the other hand is identified by its **install-ID**. By default, every new installation gets its own install and user IDs. However, it is possible to link the installation to an existing user.

To do so, we first link your app's user account \(e.g. email, UUID, etc.\) to the newly created Sentiance Platform user. Next time when the user re-installs your app, we'll use your app's user account to check for an existing link. If found, we will link this new installation to the existing user.

The biggest benefit here is the ability to get single continuous timelines for your users across app reinstalls and device migration.

## Usage

During the first initialization, the SDK will provide your app an **install-ID** associated with this particular instance of the app. In your app, you'll use this ID to link your user's account to a Sentiance user. This can only be done through server-to-server communication. Your app tells your server to contact the Sentiance Platform and request linking of your user account to this install-ID. 

{% tabs %}
{% tab title="iOS" %}
Specify a **MetaUserLinker** in the **SENTConfig**.

{% code title="Swift" %}
```swift
let metaUserLink: MetaUserLinker = { installId, linkSuccess, linkFailed in
    // Use installId to initiate a link request here, and call
    // linkSuccess() after linking succeeds.
}
let config = SENTConfig(appId: APPID, 
                        secret: SECRET, 
                        link: metaUserLink, 
                        launchOptions: launchOptions)
SENTSDK.sharedInstance().initWith(config, success: {
    // Init success
}, failure: { issue in
    // Init failed with reason <issue>
})
```
{% endcode %}

{% code title="Objective-C" %}
```objectivec
MetaUserLinker metaUserlink = ^(NSString *installId, 
  void (^linkSuccess)(void), void (^linkFailed)(void)) {
    // Use installId to initiate a link request here, and call
    // linkSuccess() after linking succeeds.
}
//SDK configuration
SENTConfig *config = [[SENTConfig alloc] initWithAppId:APPID
                                         secret:SECRET
                                         link:metaUserlink
                                         launchOptions:launchOptions];

[sdk initWithConfig:config 
            success:^{
                // Init success
            }
            failure:^(SENTInitIssue issue) {
                // Init failed with reason <issue>
            }];
```
{% endcode %}

During initialization, the SDK will pass the installID to the `MetaUserLinker`. In this method, you must initiate a link request towards the Sentiance API \(via your server\), supplying the installID and your app’s userID.

After linking succeed, call `linkSuccess()`. If it fails, you must call `linkFailed()`. The SDK initialization will then fail with reason `LINK_FAILED`. To reattempt linking, you can then initialize the SDK again, which in turn will invoke the `MetaUserLinker` a second time.
{% endtab %}

{% tab title="Android" %}
Specify a **MetaUserLinker** in the **SdkConfig**.

{% code title="Java" %}
```java
class CustomMetaUserLinker implements MetaUserLinker {
    boolean link(String installId) {
        // Use installId to initiate a link request here, and return 
        // true after linking succeeds.
  
        // This method will execute on a background thread.
    }
}
 
SdkConfig config = new SdkConfig.Builder(APP_ID, SECRET, notification)
                                ...
                                .setMetaUserLinker(metaUserLinker)
                                .build();
 
Sentiance.getInstance(this).init(config, initCallback);
```
{% endcode %}

{% code title="Kotlin" %}
```kotlin
val linker = MetaUserLinker { installId ->
    // Use installId to initiate a link request here, and return 
    // true after linking succeeds.
  
    // This method will execute on a background thread.
}

val config = SdkConfig.Builder(APP_ID, SECRET, notification)
                      ...
                      .setMetaUserLinker(linker)
                      .build()
    
Sentiance.getInstance(this).init(config, callback)
```
{% endcode %}

During initialization, the SDK will call the [`link(String)`](../api-reference/android/metauserlinker.md#link) method of your [`MetaUserLinker`](../api-reference/android/metauserlinker.md) object from a background thread, passing to it the SDK install ID. In this method, you must initiate a link request towards the Sentiance API \(via your server\), supplying the install ID and your app’s User ID.

[`link(String)`](../api-reference/android/metauserlinker.md#link) must return true only after linking with the Sentiance API succeeds. If linking fails, you must return false. The SDK initialization will then fail with reason `LINK_FAILED`.
{% endtab %}
{% endtabs %}

See our User Linking guide and the [API documentation](../../backend/rest-api/#user-link) to learn more about the server-to-server linking.

## Limitations

Sentiance allows one active installation per user. This means that multiple instances of your app can be linked to the same user, but payloads generated by only one instance will be processed by the Sentiance Platform at any given time.

Generally, the active instance is the last installed instance of the SDK. However, priority is always given to phones over tablets. If the SDK is installed on a tablet while a phone instance is active, the tablet instance will not be activated.

{% hint style="info" %}
On Android, we consider a phone to be a device having a screen size of less than 7 inches.
{% endhint %}

## Security Considerations

To ensure the security of your app and data, make sure your app is compliant with the following security guidelines.

1. Do not hardcode the Sentiance app secret in your app. Instead, securely retrieve and store it for future runs.
2. Never send linking requests to the Sentiance API directly from your app. Instead, send them through your server.
3. Use a secure connection and an authorization mechanism when sending link requests from your app to your server. This ensures that malicious requests do not get forwarded to the Sentiance API.
4. Never store the Sentiance server token in your app. This token is used for authorized communication with the Sentiance API.
5. Use certificate pinning if possible.
6. Use Android's SafetyNet Attestation to verify that requests to your server are coming from a certified apk.

## Example

An example app for both [iOS](https://github.com/sentiance/sdk-starter-ios-metauser) and [Android](https://github.com/sentiance/sdk-starter-android-metauser) can be found on our GitHub page.

