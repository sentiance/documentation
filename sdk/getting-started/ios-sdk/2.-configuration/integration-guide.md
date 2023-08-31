---
description: An optional interactive guide for integrating the Sentiance SDK
---

# Using Integration Guide

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Sentiance SDK is shipped with an optional feature to guide you through your integration process in an interactive way from Xcode. The Integration Guide diagnoses Sentiance SDK integration from Xcode during build and alerts upon issue discovery.

{% hint style="warning" %}
&#x20;Using the Integration Guide is highly recommended but is not mandatory to benefit from all the features of Sentiance SDK.
{% endhint %}

## Minimum Requirements

The minimum requirements for the Integration Guide are,

* Xcode 10,
* Python 2.7.10

## How to Activate the Integration Guide

Follow these steps below to activate the Integration Guide:

1. In Xcode, select your project and go to **Build Phases.**
2. Add a **New Run Script Phase** using the '+' sign at the top left corner.
3. Add **"/bin/sh"** at the beginning of your script, followed by a space.
4. If you are using the **SENTSDK framework**, find it in your Xcode project and **drag it** at the end of the script adding **"/Resources/.main.sh"** at the end**.**
5. If you are using the **SENTSDK xcframework**, find it in your Xcode project and **drag it** at the end of the script adding **"/IntegrationValidator/.main.sh"** at the end**.**

![](../../../../.gitbook/assets/ezgif.com-crop-4.gif)



Once the script is finished, the phase will run everytime you build your project and will notify you with the status of your integration details in **Report Navigator** panel of Xcode.

![Make sure all validation steps are shown with checkmark.](<../../../../.gitbook/assets/Screen Shot 2019-07-29 at 2.23.30 PM.png>)



