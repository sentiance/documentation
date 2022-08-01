# SdkConfig

The [`SdkConfig`](./) class allows you to specify your Sentiance app ID and secret when initializing the Sentiance SDK. This class uses the builder pattern to provide additional options and allow setting various callbacks and handlers.

## SdkConfig API

### `getAppId()`

> ```java
> String getAppId()
> ```
>
> Returns the Sentiance app credential ID.

### `getBaseURL()`

> ```java
> String getBaseURL()
> ```
>
> Returns the Sentiance API URL.

### `getMetaUserLinker()`

{% hint style="warning" %}
This method was replaced by **getUserLinker()** in v6.0.0.
{% endhint %}

> ```java
> MetaUserLinker getMetaUserLinker()
> ```
>
> Returns the [`MetaUserLinker`](../userlinker.md) used during [MetaUser linking](../../../appendix/user-linking.md).

### `getMetaUserLinkerAsync()`

{% hint style="warning" %}
This method was replaced by **getUserLinkerAsync()** in v6.0.0.
{% endhint %}

> ```java
> MetaUserLinkerAsync getMetaUserLinkerAsync()
> ```
>
> Returns the [`MetaUserLinkerAsync`](../userlinkerasync.md) used during [MetaUser linking](../../../appendix/user-linking.md).

### `getNotification()`

> ```java
> Notification getNotification()
> ```
>
> Returns a [`Notification`](https://developer.android.com/reference/android/app/Notification) used by the SDK when starting a foreground service.

### `getNotificationId()`

> ```java
> int getNotificationId()
> ```
>
> Returns the notification ID used by the SDK when starting a foreground service.

### `getOnSdkStatusUpdateHandler()`

> ```java
> OnSdkStatusUpdateHandler getOnSdkStatusUpdateHandler()
> ```
>
> Returns the [`SdkStatusUpdateHandler`](../onsdkstatusupdatehandler.md) set to receive SDK status updates.

### `getSecret()`

> ```java
> String getSecret()
> ```
>
> Returns the Sentiance app credential secret.

### `isTriggeredTripsEnabled()`

> ```java
> boolean isTriggeredTripsEnabled()
> ```
>
> Returns whether triggered trips is enabled or not.
>
> Learn more about triggered trip [here](../../../appendix/controlled-detections/controlled-trips-only.md).

### `getUserLinker()`

> ```java
> UserLinker getUserLinker()
> ```
>
> Returns the [`UserLinker`](../userlinker.md) used during [user linking](../../../appendix/user-linking.md).

### `getUserLinkerAsync()`

> ```java
> UserLinkerAsync getUserLinkerAsync()
> ```
>
> Returns the [`UserLinkerAsync`](../userlinkerasync.md) used during [user linking](../../../appendix/user-linking.md).
