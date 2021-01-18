---
description: Details about the impact of our SDK on the iOS App Store Privacy Section
---

# App Store Privacy Section

The iOS App Store requires developers to include details about the data they capture and what they do with it, in the app's privacy section. 

> "With the release of iOS/iPadOS 14.3 on Dec. 2020, any new or updated app must include a privacy label, otherwise it won't be allowed on the App Store. This requirement applies not just to third-party apps but to Apple's own programs, such as Apple Music, Apple TV, and Apple Wallet, though built-in apps aren't included."

### Where to start?

{% hint style="warning" %}
Being transparent about the data you capture is important to your users. We recommend you to keep you and your team informed and up-to-date with current and future changes to the App Store policies.
{% endhint %}

Some useful links to get started:  
[App Store - Privacy Details](https://developer.apple.com/app-store/app-privacy-details/)  
****[App Store - Privacy and user data use](https://developer.apple.com/app-store/user-privacy-and-data-use/)  
[App Store - Protecting the users' privacy ](https://developer.apple.com/documentation/uikit/protecting_the_user_s_privacy)  
[App Store - Review](https://developer.apple.com/app-store/review/)

### Data captured by our SDK

What follows will focus solely on the Sentiance SDK in relation to the new Apple privacy policy. It is important to stress that your privacy section should still be adjusted to the data captured by your specific app.

{% tabs %}
{% tab title="Health & Fitness" %}
* Used for Analytics
* Used for tracking purposes

If User Linking is **enabled:**

* Linked to the user's identity
{% endtab %}

{% tab title="Location" %}
* Used for Analytics
* Used for tracking purposes

If User Linking is **enabled:**

* Linked to the user's identity
{% endtab %}

{% tab title="Identifiers" %}
**User ID**

* Used for Analytics
* Used for tracking purposes

If User Linking is **enabled:**

* Linked to the user's identity

**Device ID**

* Used for Analytics
* Used for tracking purposes

If User Linking is **enabled:**

* Linked to the user's identity
{% endtab %}

{% tab title="Diagnostics" %}
**Crash Data**

* Used for App Functionality
* Linked to the user's identity \(if ‘User Linking’ is enabled\). 

**Performance Data**

* Used for App Functionality
* Linked to the user's identity \(if ‘User Linking’ is enabled\). 

**Other Diagnostic Data**

* Used for App Functionality
* Linked to the user's identity \(if ‘User Linking’ is enabled\).
{% endtab %}
{% endtabs %}



