# 2. Configuration

## iOS Configuration

### Project Settings

Complete the steps in the iOS [Project Settings](../ios-sdk/project-settings.md) page.

### Permissions

Set up the required permissions for iOS, as outlined in the [Permissions](../ios-sdk/7.-permissions.md) page.

## Android Configuration

### Permissions

Set up the required permissions for Android, as outlined in the [Permissions](../android-sdk/permissions.md) page.

### Customize the Notification

When running in the background, the Sentiance SDK needs to start a foreground service and supply a notification to Android, which gets shown to the user when the service is running. You can customize this notification via the **AndroidManifest.xml** file.

{% code title="AndroidManifest.xml" %}
```markup
<application ...>
    <meta-data android:name="com.sentiance.react.bridge.core.notification_id" android:value="1001"/>
    <meta-data android:name="com.sentiance.react.bridge.core.notification_title" android:resource="@string/app_name"/>
    <meta-data android:name="com.sentiance.react.bridge.core.notification_text" android:value="Touch to open."/>
    <meta-data android:name="com.sentiance.react.bridge.core.notification_icon" android:resource="@mipmap/ic_launcher"/>
    <meta-data android:name="com.sentiance.react.bridge.core.notification_channel_name" android:value="Detections"/>
    <meta-data android:name="com.sentiance.react.bridge.core.notification_channel_id" android:value="sentiance_detections"/>
    
    ...
</application>
```
{% endcode %}
