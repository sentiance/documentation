# StartTripCallback

This interface is used with [`startTrip(Map<String, String>, TransportMode, StartTripCallback)`](../sentiance.md#starttrip).

## StartTripCallback API

|  |  |
| :--- | :--- |
| void | [onSuccess](starttripcallback.md#onsuccess) \(\) |
| void | [onFailure](starttripcallback.md#onfailure) \(@Nullable [SdkStatus](../sdkstatus/) sdkStatus\) |



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
>
> | Parameters |  |
> | :--- | :--- |
> | sdkStatus | An [`SdkStatus`](../sdkstatus/) object containing the current SDK status. |



