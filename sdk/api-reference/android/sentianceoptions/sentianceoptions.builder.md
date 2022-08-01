# SentianceOptions.Builder

Builder class for SentianceOptions.

## SentianceOptions.Builder API

### `Builder`

> ```java
> Builder(Context context)
> ```
>
> Creates a builder object used for initializing the Sentiance SDK.

### `setNotification`

> ```java
> Builder setNotification(@NonNull Notification notification, int notificationId)
> ```
>
> Sets the notification that the SDK will show when running in the background, along with the notification ID. These are passed to Android's [`startForeground`](https://developer.android.com/reference/android/app/Service#startForeground\(int,%20android.app.Notification\)) method when starting a foreground service.

### `collectAppSessionData()`

> ```java
> Builder collectAppSessionData()
> ```
>
> Sets whether app session data collection is enabled. By default, it is disabled.
>
> If enabled, the SDK may collect additional sensor and location data when the app is in the foreground (i.e visible to the user). This data may get uploaded to the Sentiance Platform.

### `disableIncorrectInitializationNotification()()`

> ```java
> Builder disableIncorrectInitializationNotification()
> ```
>
> On debug builds of your app, the SDK will show a notification when it detects an incorrect SDK initialization. Use this method to disable the notification.

### `build()`

> ```java
> SentianceOptions build()
> ```
>
> Builds an `SentianceOptions` object.
