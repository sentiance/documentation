# PlayStore Location Access Review

For a general app review preparation information, please refer to [Prepare your app for review - Play Console Help](https://support.google.com/googleplay/android-developer/answer/9859455?hl=en)

### **Background Location Access Review**

The Sentiance SDK requires background location access to gather insights. Without background location access, the SDK is currently designed to seize its operation.

Effective from March 29, 2021, for existing apps, and Jan 18, 2021, for new apps, any app that uses background location needs to submit the Permissions Declaration form in Play Console which will be reviewed by Google. We anticipate that there will be a spike of review submissions around March 29, 2021, which may cause delays in publishing a new app or an update to Play Store.

[![](https://lh6.googleusercontent.com/JsIRsvqZakVDJCclutP9in0U1SO1kDNc8fp2fVnkkeQ4-0nmrPWLiOx\_7g2u7LBPftDZgRjhzz6CrS-ISihhqmmX32KKZLmhlBQRAcgtzMCxZZwW9mtKih1WldTD\_6rcpNmrJdu1)](https://www.youtube.com/watch?v=b0I1Xq\_iSK4\&feature=emb\_title)

[**Google Play Policy - Declared permissions and in-app disclosures**](https://www.youtube.com/watch?v=b0I1Xq\_iSK4\&feature=emb\_title)\*\*\*\*\\



### **Review Considerations**

Once an app is submitted for review for background location access, the below criteria will be considered at the time of writing. Please note that this is not an exhaustive list and is subject to change over time:

* Does the feature deliver clear value to the user?
* Would users expect the app to access their location in the background?
* Is the feature important to the core purpose of the app?
* Can the app deliver the same experience without accessing the location in the background?

The core functionality is defined as the main purpose of the app. This may comprise a set of core features, which must all be prominently documented and promoted in the app's description. Without the core feature(s), the app is "broken" or rendered unusable.

### **Make access to the location in the background clear to users**

* Provide a short Play Store description to signal "location" (for example, "find anywhere" or “always know where”).
* Include an in-app screenshot that shows a map/user location or geotagged images.
* If applicable, your app title or icon may also signal the location feature of your app.

### **Declaration requirements**

![](https://lh6.googleusercontent.com/0TSr-e9FPCpFa4fiqyEPDUXioSr3YciF3RLA4VBb2cw6AohIx1hGpSNRTBlmGM3b--C1rD32l6ri\_-Fba\_K3KbL7s7qkuGDjptqkfBjoFTq\_hLzkroS3hlz2zSUE1pCsZgvlLnM5)

When completing the permissions declaration form (above), you’ll also need to complete the steps below so Google can evaluate your app’s access to the location in the background.

As part of the permissions declaration, you must provide a link to a short video that demonstrates the location-based feature in your app that requires access to the location in the background. Without the video, the app will be rejected.

[![](https://lh4.googleusercontent.com/WbZ-3v4rSrMxFxYQkbg7oPxUhAZ\_cJA0OTZG0FEYXfoSJ7aTyezxx7of6JwBmMP\_5-DafttqA6X10rUbkfiGQ0DfZENTCyarvAzNXo4Itet0Bx4di6jNEE-GnhFg-BpWnR1VK57k)](https://www.youtube.com/watch?v=z35PrureI1w\&feature=emb\_title)

[**Play Policy Location in the background**](https://www.youtube.com/watch?v=z35PrureI1w\&feature=emb\_title)

The video should demonstrate the background location feature and the required steps to encounter and enable this feature in-app. The video should show:

* Runtime prompt
* The prominent in-app disclosure dialogue displayed to users
* The feature is activated from the background

The recommended duration is 30 seconds or less, and it does not need to be an exhaustive app demo. Rather, focus on conciseness and clarity of why the background location is needed. A YouTube link is the preferred video format.

### **In-app disclosure**

If your app accesses a location in the background, you must provide an in-app disclosure of your data access, collection, use, and sharing.

#### Requirements

* Must be within the app itself, not only in the app description or on a website;
* Must be displayed in the normal usage of the app and not require the user to navigate into a menu or settings;
* Must describe the data being accessed or collected;
* Must explain how the data will be used and/or shared;
* Cannot only be placed in a privacy policy or terms of service; and
* Cannot be included with other Disclosures unrelated to personal or sensitive data collection.
* Does not need explicit consent such as an “accept” or “I understand” granted by the user as this is done in the runtime prompt that immediately follows; enabling the user to close or swipe away are acceptable ways to migrate out of the disclosure.

The language in the disclosure MUST include the following elements:

1. The term “location.”
2. An indication that the nature of usage is in the background by using one of the following phrases “background” / “when the app is closed” / “always in use” / “when the app is not in use.”
3. A list of all the features that use location in the background.
4. If you extend permitted usage to ads, you must include the following: “used to provide ads/support advertising/support ads.” (Choose the most accurate phrasing).

#### **Example disclosure statements**

Below is an example statement that can be used in your disclosure.

“\[This app] collects location data to enable \["feature"], \["feature"], & \["feature"] even when the app is closed or not in use.”

### **Privacy policy**

Adding a privacy policy to your app's store listing helps provide transparency about how you treat sensitive user and device data. The privacy policy must, together with any in-app disclosures, comprehensively disclose how your app collects, uses, and shares user data, including the types of parties with whom it is shared. You should consult your own legal representative to advise you of what is required.

* You must link to a privacy policy on your app's store listing page and within your app.
* Make sure your privacy policy is available on an active URL, applies to your app, and specifically covers user privacy.
* If your app uses a location in the background, your privacy policy must contain appropriate related disclosures.
* Ensure your privacy policy page is clearly labeled.

### **Enforcement**

“By publishing to Google Play, you agree to adhere to the [Google Play Program Policies](https://play.google.com/about/developer-content-policy.html) and [Developer Distribution Agreement](https://play.google.com/about/developer-distribution-agreement.html). Google is not required to send you a warning prior to suspension or termination.”

App rejection can happen if the criteria above are not met. Once an app is rejected, do not resubmit the app until the violation has been fixed.

There have been (unverified) cases reported that Google Play would suspend the account if an app is rejected consecutively for the same reason and this may incur irreversible damage to your account.

This video will help [How to handle a policy violation on Google Play](https://www.youtube.com/watch?v=xjRqFbTHUOQ\&feature=youtu.be)\*\*\*\*\\



### **References**

* [Requesting access to location in the background - Play Console Help (google.com)](https://support.google.com/googleplay/android-developer/answer/9799150)
* [Tips for getting your app approved for background location access](https://android-developers.googleblog.com/2020/11/tips-for-getting-your-app-approved-for-background-location-access.html)
* [New guidelines for accessing background location in Android](https://medium.com/@adrian.kajda/new-guidelines-for-accessing-background-location-in-android-d2e07d45ae79)
* [Google Play Developer Policy Center](https://play.google.com/about/developer-content-policy/)
* [Prepare your app for review - Play Console Help](https://support.google.com/googleplay/android-developer/answer/9859455?hl=en)
* [My app has been removed from Google Play - Play Console Help](https://support.google.com/googleplay/android-developer/answer/2477981)
*   [Enforcement Process - Play Console Help](https://support.google.com/googleplay/android-developer/answer/9899234?hl=en)\
    \
    \
    \\

