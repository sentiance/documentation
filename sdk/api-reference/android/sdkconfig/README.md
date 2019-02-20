# SdkConfig

The [`SdkConfig`](./) class allows you to specify your Sentiance app ID and secret when initializing the Sentiance SDK. This class uses the builder pattern to provide additional options and allow setting various callbacks and handlers.

## SdkConfig API

|  |  |
| :--- | :--- |
| String | [getAppId](./#getappid) \(\) |
| [MetaUserLinker](../metauserlinker.md)  | [getMetaUserLinker](./#getmetauserlinker) \(\) |
| Notification  | [getNotification](./#getnotification) \(\) |
| int  | [getNotificationId](./#getnotificationid) \(\) |
| [OnSdkStatusUpdateHandler](../onsdkstatusupdatehandler.md)  | [getOnSdkStatusUpdateHandler](./#getonsdkstatusupdatehandler) \(\) |
| String  | [getSecret](./#getsecret) \(\) |
| boolean  | [isTriggeredTripsEnabled](./#istriggeredtripsenabled) \(\) |



### `getAppId()`

> ```java
> String getAppId()
> ```
>
> Returns the Sentiance app credential ID.

### `getMetaUserLinker()`

> ```java
> MetaUserLinker getMetaUserLinker()
> ```
>
> Returns the [`MetaUserLinker`](../metauserlinker.md) used by the SDK for meta-user linking.
>
> Learn more about Meta-Users [here](../../../appendix/meta-users.md).

### `getNotification()`

> ```java
> Notification getNotification()
> ```
>
> Returns a [`Notification`](https://developer.android.com/reference/android/app/Notification) object used by the SDK when starting a foreground service.

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
