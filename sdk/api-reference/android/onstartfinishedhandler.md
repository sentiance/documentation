# OnStartFinishedHandler

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

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
