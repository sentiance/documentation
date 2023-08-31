# StartTripCallback

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`startTrip(Map<String, String>, TransportMode, StartTripCallback)`](../sentiance.md#starttrip).

## StartTripCallback API

### `onSuccess()`

> ```java
> void onSuccess()
> ```
>
> Called when a trip is successfully started.

### `onFailure()`

> ```java
> void onFailure(@Nullable SdkStatus sdkStatus)
> ```
>
> Called when a trip start fails. Check the [`SdkStatus`](../sdkstatus/) object to find out why.

| Parameters |                                                                           |
| ---------- | ------------------------------------------------------------------------- |
| sdkStatus  | An [`SdkStatus`](../sdkstatus/) object containing the current SDK status. |

