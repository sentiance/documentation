---
description: User Creation On the SDK
---

# User Creation

Each Sentiance user is linked to a unique user on your system. When creating a new Sentiance user, we ask you to provide to us an identifier that points to a unique user in your system.

The process of linking your system user to a Sentiance user requires a server-to-server interaction. The Sentiance SDK does not accept your system's user identifier directly. In order for us to do the user linking, we need a trusted source to provide us the user identifier. We do not consider a mobile app to be a trusted source. Instead, we require you to send the request from your server, and use a Sentiance API Key to authenticate it. You can generate this API key in our [Insights Dashboard](https://insights.sentiance.com/). You must **never transmit** this key to your app.

### Requesting an Authentication Code

You provide to us your system user identifier when making an [authentication code request](../../backend/rest-api/#authentication-code). In return, Sentiance will provide to you a short-lived authentication code, which you will then use to create a Sentiance user on the device.

The steps are as follows:

1. When decided to create a Sentiance user, contact your backend and request a Sentiance authentication code.
2. On your backend, [create a corresponding request](../../backend/rest-api/#authentication-code) towards the Sentiance backend, which will include your user's unique identifier. This request is authenticated using a Sentiance API Key.
3. Retrieve the authentication code provided by Sentiance and forward it to your app.
4. In the app, create a Sentiance user by passing this authentication code.

### Creating a User On the Device

Once you have retrieved the authentication code, pass it to the SDK's user creation method. The SDK will make a request towards the Sentiance backend, which will include this code and some additional information about your app and the device. In return, the Sentiance backend will respond with a unique Sentiance user identifier, and an SDK configuration.

{% tabs %}
{% tab title="iOS" %}
```swift
let options = SENTUserCreationOptions(authenticationCode: "authCode you received")

Sentiance.shared.createUser(options: options) { result, error in
    guard let result = result else {
    print ("Error: \(error!.failureReason)")
    }
    
    // Use result
}
```
{% endtab %}

{% tab title="Android" %}
```kotlin
val options = UserCreationOptions.Builder(authenticationCode).build()

Sentiance.getInstance(context).createUser(options).addOnCompleteListener { operation ->
    if (operation.isSuccessful) {
        val userInfo = operation.result.userInfo
        Log.d(TAG, "Created a user with ID: ${userInfo.userId}")
    } else {
        val error = operation.error
        Log.e(TAG, "User creation failed with reason ${error.reason.name}. Details: ${error.details}")
    }

```
{% endtab %}

{% tab title="React Native" %}
```javascript
import { createUser } from '@sentiance-react-native/core';

try {
    const result = await createUser({ authCode: authenticationCode });
    console.log(`Created a user with ID: ${result.userInfo.userId}`);
} catch(e) {
    console.log(`User creation failed with error: ${e}`);
}
```
{% endtab %}
{% endtabs %}

### Multi-User Support

The SDK supports the presence of only one Sentiance user on the device at a time. If your app supports multiple users (e.g. via a login flow), you can utilize the SDK's `reset` functionality to remove the existing user from the device, before creating a new one.

### User Restoration

We realize that users can migrate to different devices, or reinstall your app on the same device. As such, we support restoring a Sentiance user during user creation.

During the authentication code request, when you provide to us your system user identifier, we will first look up to see whether this ID is already linked to an existing Sentiance user. If so, we will not create a new Sentiance user. Instead, we will provide to you an authentication code that is linked to the existing Sentiance user. When the SDK forwards this code to our backend, we will restore this existing Sentiance user instead.

{% hint style="info" %}
Per user, we support only one active device at any time. Therefore, when you restore a Sentiance user on a device, any other SDK instance that has the same Sentiance user will be deactivated.

The only exception to this is when the existing active user instance is on a _phone_ device, and you attempt to restore the user on a _tablet_ device. In this case, Sentiance will prefer the phone device, and keep the user active on the phone.
{% endhint %}
