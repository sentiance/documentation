# StopTripCallback

This interface is used with [`stopTrip(StopTripCallback)`](../sentiance.md#starttrip).

## StopTripCallback API

### `onSuccess()`

> ```java
> void onSuccess()
> ```
>
> Called when an external trip is successfully stopped.

### `onFailure()`

> ```java
> void onFailure(@Nullable SdkStatus sdkStatus)
> ```
>
> Called when a trip stop fails. Check the [`SdkStatus`](../sdkstatus/) object to find out why.
>
> This method is also called when [`stopTrip(StopTripCallback)`](../sentiance.md#stoptrip) is called while no external trip exists. To check if there is an ongoing external trip, call [`isTripOngoing()`](../sentiance.md#istripongoing).

| Parameters |                                                                           |
| ---------- | ------------------------------------------------------------------------- |
| sdkStatus  | An [`SdkStatus`](../sdkstatus/) object containing the current SDK status. |
