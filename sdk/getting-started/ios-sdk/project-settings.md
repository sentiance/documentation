# 2. Project Settings

After adding the SDK, you need to configure your project to prepare it before starting to use the SDK.

## Configuring Capabilities

1. Go to the **Capabilities** tab of your target settings
2. Under **Background Modes**, enable **Location updates**, **Background fetch**, and **Background processing**.

![](../../../.gitbook/assets/xcode\_capabilities.png)

## Setting Up Background Tasks

Add the following background task identifiers to the project info (Info.plist):

* com.sentiance.backgroundtask.tilerefresh
* com.sentiance.backgroundtask.task\_processing

Add the following task identifier if you plan to utilize the step counting SDK feature (disabled by default):

* com.sentiance.backgroundtask.step\_counter

{% hint style="info" %}
You can add these identifier by following these steps:

1. Project settings -> select a target -> Info.
2. Add "Permitted background task scheduler identifiers".
3. Add the above identifiers as sub-items.
{% endhint %}
