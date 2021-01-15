---
description: Details about the impact of our SDK on the iOS App Store Privacy Section
---

# App Store Privacy Section

The iOS App Store requires developers to include details about the data they capture and what they do with it, in the App Store privacy section. 

> "With the release of iOS/iPadOS 14.3 on Dec. 2020, any new or updated app must include a privacy label, otherwise it won't be allowed on the App Store. This requirement applies not just to third-party apps but to Apple's own programs, such as Apple Music, Apple TV, and Apple Wallet, though built-in apps aren't included."

### Where to start?

Being transparent about the data you capture is important to your users. We recommend you to keep you and your team informed and up-to-date with current and future changes to the App Store policies. Some useful links to get started:  
[App Store - Privacy Details](https://developer.apple.com/app-store/app-privacy-details/)  
****[App Store - Privacy and user data use](https://developer.apple.com/app-store/user-privacy-and-data-use/)  
[App Store - Protecting the users' privacy ](https://developer.apple.com/documentation/uikit/protecting_the_user_s_privacy)  
[App Store - Review](https://developer.apple.com/app-store/review/)

### Data captured by our SDK

What follows will focus solely on the Sentiance SDK in relation to the new Apple privacy policy. It is important to stress that your privacy section should still be adjusted to the data captured by your specific app.  


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Health &amp; Fitness</b>
      </th>
      <th style="text-align:left"><b>Location</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>Used for Analytics</p>
        <p>Linked to the user&apos;s identity (if &#x2018;User Linking&#x2019; is
          enabled).</p>
        <p>Used for tracking purposes</p>
      </td>
      <td style="text-align:left">
        <p>Used for Analytics</p>
        <p>Linked to the user&apos;s identity (if &#x2018;User Linking&#x2019; is
          enabled).</p>
        <p>Used for tracking purposes</p>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Identifiers</th>
      <th style="text-align:left">Diagnostics</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>User ID</b>
        </p>
        <p>Used for Analytics</p>
        <p>Linked to the user&apos;s identity (if &#x2018;User Linking&#x2019; is
          enabled).</p>
        <p>Used for tracking purposes</p>
      </td>
      <td style="text-align:left">
        <p><b>Crash Data</b>
        </p>
        <p>Used for App Functionality</p>
        <p>Linked to the user&apos;s identity (if &#x2018;User Linking&#x2019; is
          enabled).</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Device ID</b>
        </p>
        <p>Used for Analytics</p>
        <p>Linked to the user&apos;s identity (if &#x2018;User Linking&#x2019; is
          enabled).</p>
        <p>Used for tracking purposes</p>
      </td>
      <td style="text-align:left">
        <p><b>Performance Data</b>
        </p>
        <p>Used for App Functionality</p>
        <p>Linked to the user&apos;s identity (if &#x2018;User Linking&#x2019; is
          enabled).</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><b>Other Diagnostic Data</b>
        </p>
        <p>Used for App FunctionalityLinked to the user&apos;s identity (if &#x2018;User
          Linking&#x2019; is enabled).</p>
      </td>
    </tr>
  </tbody>
</table>



