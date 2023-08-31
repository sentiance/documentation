# Privacy Report & Dashboard

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

A personal device and the apps need to gain trust from its users when it comes to personal and sensitive information. In iOS 15 and Android 12, both Apple and Google are expanding their commitment to privacy and data access transparency to their users and Sentiance welcomes this change.

Sentiance is committed to handle user data with a high level of confidentiality, and use the data for the good of people. Also, Sentiance provides full transparency and control when it comes to user data. We encourage our clients to be fully transparent about the use of data and how it adds value to their end-users.

### iOS 15 and App Privacy Report

iOS 15 have a new section in the privacy settings called [**App Privacy Report**](https://www.apple.com/newsroom/2021/06/apple-advances-its-privacy-leadership-with-ios-15-ipados-15-macos-monterey-and-watchos-8/#:\~:text=Check%20Up%20on%20App%20Privacy)**.** Disclosing to the users how often and when any apps use data like location, photos, camera, microphone, and contacts in the last seven days. It transparently shows which domains and when an app has contacted other domains. Sentiance SDK access location data and contacts Sentiance API to upload the collected data. Therefore, once Sentiance SDK is integrated into your app, the Report will disclose when the location data were accessed and that it has contacted Sentiance API.

![](<../.gitbook/assets/Untitled drawing (1).png>)

### Android 12 and Privacy Dashboard

To provide more transparency on when and what data are used, Google has added a new section with a timeline view of the last 24-hour access to location, microphone, and camera. Sentiance SDK access location data and the timing of location data access are disclosed in the Privacy Dashboard.

To audit that your app and the third-party SDKs within the app are using the right amount of data at the right time, you can use [Data access auditing APIs](https://developer.android.com/guide/topics/data/audit-access) (Added in Android 11) which makes it easy to identify which part of the code access user's private data.

![](../.gitbook/assets/untitled.gif)



### What does this mean?

Users are more likely to disable location permission unless a compelling value proposition is presented in a clear way. We encourage our clients to consider the best practices listed below.

{% embed url="https://developer.apple.com/design/human-interface-guidelines/ios/app-architecture/accessing-user-data/" %}

{% embed url="https://developer.android.com/training/location" %}

Also, check if the correct permissions are authorized at every app start. If the permissions are not authorized or incorrect, then nudge the user to enable or correct the location settings.&#x20;

Without the full location permission, Sentiance SDK will not start and this can be checked through SDKStatus objects.

{% embed url="https://docs.sentiance.com/sdk/api-reference/android/sdkstatus" %}

{% embed url="https://docs.sentiance.com/sdk/api-reference/ios/sentsdk#getsdkstatus" %}





## References

* [What’s new in Android Privacy 18 May 2021](https://android-developers.googleblog.com/2021/05/android-security-and-privacy-recap.html)
* [Apple advances its privacy leadership with iOS 15, iPadOS 15, macOS Monterey, and watchOS 8](https://www.apple.com/newsroom/2021/06/apple-advances-its-privacy-leadership-with-ios-15-ipados-15-macos-monterey-and-watchos-8)

