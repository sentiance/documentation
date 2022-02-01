# Notification Management

When specifying a channel/priority for the SDK notification, use a separate channel/priority configured to show non-intrusive notifications. When the SDK is running, your application should show a subtle notification icon, with an appropriate message informing your users about the ongoing detection.

Setting the channel importance to `IMPORTANCE_LOW` and the notification priority to `PRIORITY_MIN` will create notifications that do not pop up in front of the user, or cause sounds and device vibrations. The goal is to not distract the user every time the Sentiance SDK runs, as this will cause frustration and lead to eventual app removal.

Properly wording your notification is also important to let your users know why your application is running. State what value you are adding to your user at that moment. For example:

> **Journeys is running**  
> Working in the background to improve your driving habits

Finally, it's important to let your users know that they can easily prioritize and disable notifications. Using the following snippet on Android 8 and above, you can take your user to the channel configuration setting directly from within your app:

```java
Intent intent = new Intent(Settings.ACTION_CHANNEL_NOTIFICATION_SETTINGS)
		.putExtra(Settings.EXTRA_APP_PACKAGE, context.getPackageName())
		.putExtra(Settings.EXTRA_CHANNEL_ID, channelId);
startActivity(intent);
```

For more on notification channel best practices, check out Android's [design guidelines](https://material.io/design/platform-guidance/android-notifications.html#settings).

