# Android 10 Update Behavior

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

If you are still targeting API level 28 or lower, read the following information to understand the impact of upgrading to Android 10 on the location and activity recognition permissions.

## Location Permission

![](../../../.gitbook/assets/Android10\_location.png)

### Summary

The sooner you add the background location permission to your app, the better. This is because after an Android 10 upgrade, you will benefit from the auto-granted background location access (see #2.1 above). However, the caveat is that if a user has already upgraded to Android 10, updating to this new version of your app that includes the new permission will cause the auto-granted background access to be revoked, regardless of the app's target API level (see #1.1.3 above).

So you have two options:

1. Add the new background location permission to your app now (while Android 10 population is low) and benefit from the auto-granted access as your users upgrade to Android 10, but you'll need to handle your existing Android 10 users by asking them to re-grant the background location access permission, or
2. postpone adding the new permission and benefit from the auto-granted background location access for your existing and upgrading Android 10 users, however, once deciding to update your app's target API level to 29, add the new permission and ask all your Android 10 users to re-grant the background location permission.

## Activity Recognition Permission

`com.goo...ACTIVITY_RECOGNITION` represents Google Play Services' activity recognition permission, which is already added to your app by the Sentiance SDK.

![](<../../../.gitbook/assets/Android10\_activity (1).png>)

### Summary

If you're still targeting API level 28 and lower, there's no special benefit in adding the new activity recognition permission to your app. There is a down side though. You lose the install-time auto-granted access for new installations on Android 10 (see #4.2 above). You can wait until after targeting API level 29, but after doing so, remember to handle fresh Android 10 installations by asking your users to explicitly grant the permission.

If you're already targeting API level 29, add the permission to your manifest and ask your users to grant it.
