# UserActivityListener

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`setUserActivityListener(UserActivityListener)`](sentiance.md#setuseractivitylistener).

## UserActivityListener API

### `onUserActivityChange()`

> ```java
> void onUserActivityChange(UserActivity activity)
> ```
>
> Called whenever a new [`UserActivity`](useractivity.md) is created.
