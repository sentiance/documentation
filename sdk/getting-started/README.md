# Getting Started

{% hint style="success" %}
You can find us on [Github](https://github.com/sentiance/).
{% endhint %}

{% hint style="info" %}
**Make sure to think about your development environments before you get started**

It is a best practice to use multiple environments during the development of your apps (Development, Testing, Production, etc.)&#x20;

You will need a separate app id & secret for each of these environments, make sure to mention this in your request.

This will also allow us to enable debugging & analytics on your development environment if necessary.
{% endhint %}

### Requesting an app id & secret

In order to properly integrate the Sentiance SDK you will need an app id & secret. You can request these by emailing to [support@sentiance.com](mailto:support@sentiance.com) or your Sentiance project point of contact.

{% hint style="danger" %}
The app ID and secret are sensitive information and **must not be shared or communicated** back to Sentiance or outside of your company in any event (e.g. via email, or Slack communication).
{% endhint %}

{% hint style="warning" %}
Please note that we don't recommend hard-coding the appID and secret key in your app. This is not secure and can lead to leaked credentials. Please load these credentials from a secure source such a remote server, and store them securely on the device.
{% endhint %}

### Getting your app credentials

1. Head over to[ insights.sentiance.com/#/](http://insights.sentiance.com/#/)
2. You should see at least one cell with the name of your app or company
   * You may see one per development environment as mentioned above.
3. The first field contains your app id & an easy copy button
4. Click on "Click to reveal" under app secret
5. You will now have an appID & secret key ready for integrating the Sentiance SDK into your mobile application

{% hint style="warning" %}
In order to perform the above steps you will need developer permissions for your app / company.
{% endhint %}
