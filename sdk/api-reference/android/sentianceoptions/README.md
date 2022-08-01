# SentianceOptions

The SentianceOptions class allows you to specify SDK initialization options. This class is used with [`Sentiance.initialize(SentianceOptions)`](../sentiance.md.md#initialize-sentianceoptions).

See: SentianceOptions.Builder.

## SentianceOptions API

### `getNotificationId()`

> ```java
> int getNotificationId()
> ```
>
> Returns the ID of the notification that the SDK will show when running in the background. This ID is passed to Android's [`startForeground`](https://developer.android.com/reference/android/app/Service#startForeground\(int,%20android.app.Notification\)) method when starting a foreground service.

### `getNotification()`

> ```java
> Notification getNotification()
> ```
>
> Returns the notification that the SDK will show when running in the background. This notification is passed to Android's [`startForeground`](https://developer.android.com/reference/android/app/Service#startForeground\(int,%20android.app.Notification\)) method when starting a foreground service.

### `isAppSessionDataCollectionEnabled()`

> ```java
> boolean isAppSessionDataCollectionEnabled()
> ```
>
> Returns whether app session data collection should be enabled.
>
> If enabled, the SDK may collect additional sensor and location data when the app is in the foreground (i.e visible to the user). This data may get uploaded to the Sentiance Platform.

### `isIncorrectInitializationNotificationDisabled()`

> ```java
> boolean isIncorrectInitializationNotificationDisabled()
> ```
>
> Returns whether incorrect SDK initialization notifications should be enabled. On debug builds of your app, the SDK can show a notification when it detects an incorrect SDK initialization.
