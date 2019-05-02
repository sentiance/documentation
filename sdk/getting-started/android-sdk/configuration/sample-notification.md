# Sample Notification

The example below shows how to create a notification that can be passed to [`SdkConfig.Builder`](../../../api-reference/android/sdkconfig/sdkconfig-builder.md). We use the `android.support.v7.app.NotificationCompat` class to build a notification suitable for both old and new Android versions.

The notification channel, necessary for Android 8 and above, has the channel importance set to `IMPORTANCE_LOW`, the minimum [recommended](https://developer.android.com/reference/android/app/NotificationManager#IMPORTANCE_MIN) by Google for notifications used for running services.

```java
private Notification createNotification() {
    // PendingIntent that will start your application's MainActivity
    Intent intent = new Intent(context, MainActivity.class);
    PendingIntent pendingIntent = PendingIntent.getActivity(context, 0, intent, 0);
     
    // On Oreo and above, you must create a notification channel
    String channelId = "channel-id";
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId, "Channel name", NotificationManager.IMPORTANCE_LOW);
        channel.setShowBadge(false);
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        notificationManager.createNotificationChannel(channel);
    }

    return new NotificationCompat.Builder(context, channelId)
            .setContentTitle(context.getString(R.string.app_name) + " is running")
                .setContentText("Touch to open.")
                .setContentIntent(pendingIntent)
                .setShowWhen(false)
                .setSmallIcon(R.mipmap.ic_launcher)
                .setPriority(NotificationCompat.PRIORITY_MIN)
                .build();
}
```

{% hint style="info" %}
You can quickly test the notification appearance by running a fresh SDK install on an Android Oreo device. The notification will appear the first time the SDK starts automatic detections, or when you manually start a trip. More about this [here](../../../appendix/controlled-detections/).
{% endhint %}



