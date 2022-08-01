# SdkStatusUpdateListener

A listener that receives SDK status updates. See how it's used [here](../../getting-started/react-native-quick-start/6.-sdk-status-updates.md).

## SdkStatusUpdateListener API

### `onSdkStatusUpdate`

> ```java
> void onSdkStatusUpdate(SdkStatus status)
> ```
>
> Called whenever the SDK status changes (or more specifically, whenever one of the fields of [`SdkStatus`](sdkstatus/) changes).

| Parameters |                                                                          |
| ---------- | ------------------------------------------------------------------------ |
| status     | An [`Sdkstatus`](sdkstatus/) object representing the current SDK status. |
