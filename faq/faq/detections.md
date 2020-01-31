---
description: Frequently asked questions about false or missing detections.
---

# Detections \(FAQ\)

## Why is there no data for a specific timeline?

**I have installed the app less than 3 days ago**  
Our platform needs a certain amount of data before we can start identifying your events, moments & segments correctly. Please make sure you've been tracking with the permissions set correctly for at least a few days. 

**I have installed the app more than 3 days ago**  
Make sure your device has the required specifications.  
Make sure you've given the right [permissions](../../sdk/getting-started/android-sdk/permissions.md). 

Also, specific android devices may require whitelisting.  
If none of this works or you need more information, contact [support@sentiance.com](mailto:support@sentiance.com) for assistance.

## **Why does a specific trip not show up on a timeline?**

There can be multiple reasons for a trip not showing up on your timeline:

* The trip was too short in duration \(&lt;5min\)
* The trip was too short in distance \(&lt;2km\)
* The phone was in flight mode during the trip
* The phone was in low battery mode \(only on certain Android phones\) during the trip
* The app did not get the required permissions \(always on\) during the trip

## **Why was phone usage falsely detected during a trip?**

Our algorithm that detects phone usage while driving might sometimes detect phone usage incorrectly. This is usually the result of a phone moving in the pocket while driving, or hitting a sequence of speed bumps on a certain trajectory. 

## **Why do some trips change after a few days?**

When we are processing trips in real-time, we might not always have all the required information to provide accurate detections. As a result, we offer a preliminary result based on the available information. Sometimes we receive information after a trip that will make us reprocess the trip to provide a better result. To read more about retroactively changing trips, look [here](https://www.sentiance.com/2019/07/03/when-context-is-king-time-is-queen/).  


