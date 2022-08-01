# Getting Started

{% hint style="success" %}
You can find us on [Github](https://github.com/sentiance/).
{% endhint %}

{% hint style="info" %}
**Make sure to think about your development environments before you get started**

It is a best practice to use multiple environments during the development of your apps (Development, Testing, Production, etc.)&#x20;

You will need a separate app that are defined on the Sentiance Platform for each of these environments, make sure to mention this in your request.

This will also allow us to enable debugging & analytics on your development environment if necessary.
{% endhint %}

### Requesting an app

In order to properly integrate the Sentiance SDK, you will need an app that is defined on the Sentiance Platform. An app has a unique set of credentials (app ID & secret) and API keys which you will use during your integration. You can request an app by emailing to [support@sentiance.com](mailto:support@sentiance.com) or your Sentiance project point of contact.

{% hint style="danger" %}
Sentiance API keys are used for creating users on the Sentiance Platform, or querying user data. These keys are used for authenticating requests coming to the Sentiance Platform from your backend. You must **never embed or transmit** API keys to your app, as this can lead to leaked keys.

App credentials (app ID and secret) can be used to create unlinked Sentiance users directly from your app. We **strongly advise** not to hard-code app credentials in your app. Instead, load these credentials from a secure source, such as a remote server, only when necessary.
{% endhint %}

{% hint style="danger" %}
The app ID and secret are sensitive information and **must not be shared or communicated** back to Sentiance or outside of your company in any event (e.g. via email, or Slack communication).

We also advise against hard-coding the appID and secret key in your app. This is not secure and can lead to leaked credentials. Please load these credentials from a secure source such a remote server, and store them securely on the device.
{% endhint %}

### Getting access to app credentials and keys

1. Head over to[ insights.sentiance.com/#/](http://insights.sentiance.com/#/)
2. You should see at least one cell with the name of your app or company. You may see one per development environment as mentioned above.
3. The first field contains your app ID & an easy copy button.
4. Click on "Click to reveal" under app secret.
5. You will now have an app ID and a secret key which can be used for creating Sentiance users directly from your app. This approach is less secure however, and we recommend continuing with the below steps.
6. Click the 3 dots on the bottom right of your app, and choose "API Keys" from the menu.
7. In the API key management page, click on the top right "Create API Key" button.
8. In the new popup dialog, enter a name for your key, and check "User Link." This will grant user creation privileges to this key.
9. Click "create." You can now download your keys or click on "API KEYS" to copy them to your clipboard.
10. Use this key to authenticate your user creation requests towards the Sentiance API. For more on this, see [here](../../backend/rest-api/#authentication-code).

{% hint style="warning" %}
In order to perform the above steps you will need developer permissions for your app / company.
{% endhint %}
