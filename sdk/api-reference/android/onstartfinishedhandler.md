# OnStartFinishedHandler

This interface is used with [`start(OnStartFinishedHandler)`](sentiance.md#start).

## OnStartFinishedHandler API

### OnStartFinished

> ```java
> void onStartFinished(SdkStatus sdkStatus)
> ```
>
> Called when the SDK start operation has finished. This does not guarantee that detections are actually occurring; to know that, check the [`SdkStatus`](sdkstatus/) parameter.

| Parameters |                                                                          |
| ---------- | ------------------------------------------------------------------------ |
| status     | An [`Sdkstatus`](sdkstatus/) object representing the current SDK status. |
