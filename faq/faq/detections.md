---
description: Frequently asked questions about false or missing detections.
---

# Detections (FAQ)

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Why is there no data for a specific timeline?

**I have installed the app less than 3 days ago**\
****Our platform needs a certain amount of data before we can start identifying your events, moments & segments correctly. Please make sure you've been tracking with the permissions set correctly for at least a few days. Specific venues, like home and work, could take up to a week to detect correctly.

**I have installed the app more than 3 days ago**\
Make sure your device has the required specifications.\
Make sure you've given the right [permissions](../../sdk/getting-started/android-sdk/permissions.md).&#x20;

Also, specific android devices may require whitelisting.\
If none of this works or you need more information, contact [support@sentiance.com](mailto:support@sentiance.com) for assistance.

## **Why is a trip incorrectly or not detected?**

Both short trips and long trips will be correctly detected in almost all cases. When a trip is incorrectly detected or not detected at all, it might be because:

*   The phone was in flight mode during the trip.

    The trip was very short in duration (< 3 min).
* The trip was very short in distance (< 2 km or 1.25 mi).
* The phone was in a battery saving mode during the trip.
* The app did not get the required permissions (always on) during the trip.

## **Why was phone usage falsely detected during a trip?**

Our algorithm that detects phone usage while driving might sometimes detect phone usage when the phone is moving in the pocket while driving, or when it hits a sequence of speed bumps.&#x20;

## **Why do some trips change after a few days?**

When we are processing trips in real-time, we might not always have all the required information to provide accurate detections. As a result, we offer a preliminary result based on the available information. Sometimes we receive information after a trip that will make us reprocess the trip to provide a better result. To read more about retroactively changing trips, look [here](https://www.sentiance.com/2019/07/03/when-context-is-king-time-is-queen/).\
