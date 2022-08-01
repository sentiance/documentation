# Sample Notification

The example below shows how to create a notification that can be passed to `SentianceOptions`. We use the `androidx.core.app.NotificationCompat` class to build a notification suitable for both old and recent Android versions.

The notification channel, necessary for Android 8 and above, has the channel importance set to `IMPORTANCE_LOW`, the minimum [recommended](https://developer.android.com/reference/android/app/NotificationManager#IMPORTANCE\_MIN) by Google for notifications used for running services.

```java
private fun createNotification(): Notification {
    // PendingIntent that will start your application's MainActivity
    val intent = Intent(context, MainActivity::class.java)
    val pendingIntent = PendingIntent.getActivity(context, 0, intent, PendingIntent.FLAG_IMMUTABLE)

    // On Oreo and above, you must create a notification channel
    val channelId = "background_detections"
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        val channel = NotificationChannel(channelId, "Background Detections", NotificationManager.IMPORTANCE_LOW)
        channel.setShowBadge(false)
        val notificationManager = context.getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager
        notificationManager.createNotificationChannel(channel)
    }
    return Builder(context, channelId)
        .setContentTitle(context.getString(R.string.app_name).toString() + " is running")
        .setContentText("Touch to open.")
        .setContentIntent(pendingIntent)
        .setShowWhen(false)
        .setSmallIcon(R.mipmap.ic_launcher)
        .setPriority(NotificationCompat.PRIORITY_MIN)
        .build()
}
```

{% hint style="info" %}
You can quickly test the notification appearance by running a fresh app/SDK installation on an Android 8+ device. The notification will appear the first time the SDK starts automatic detections, or when you manually start a trip (more about this [here](../controlled-detections/automatic-detections-with-forced-trips.md)).
{% endhint %}

