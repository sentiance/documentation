---
description: >-
  Frequently asked questions about getting started with the Sentiance SDK and
  getting through the integration process.
---

# Integration \(FAQ\)

## How do I know if the integration was successful?

We always suggest to our clients to collect data from as many users as possible for at least a few days and then compare with our Journeys app for ground-truth. When the timelines in your app and Journeys look the same, you can be fairly confident that the integration was successful. For more detailed steps, look [here](https://docs.sentiance.com/guide/verifying-your-integration).

## **How can I test if user linking works for my app**?

You can find all the steps required to set up user linking [here](../../important-topics/user-linking-2.0.md). After you have received a success callback, you can start testing it with real devices. We suggest to:

1. [ ] Install the app with the Sentiance SDK
2. [ ] Make an account 
3. [ ] Send at least one stationary and one trip
4. [ ] Reinstall the app on the same device
5. [ ] Log in to the same account
6. [ ] Send at least one stationary and one trip
7. [ ] Check the timeline of the user to see if they show data for both installs

It is recommended to do this for both iOS and Android and to perform multiple installs on multiple devices. When all of these are successful, you can be fairly confident user linking was successful.

## When does UserID get deleted?

Once a UserID is generated, it's stored within the device. There are three cases where Sentiance UserID is removed from the device. The cases are:

1. Resetting the SDK \(calling reset\(\)\).
2. Deleting the cache from the app settings.
3. Uninstalling and installing the app again.



