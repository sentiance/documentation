# OnSdkStatusUpdateHandler

This interface is used with [`setOnSdkStatusUpdateHandler(OnSdkStatusUpdateHandler)`](sdkconfig/sdkconfig-builder.md#setonsdkstatusupdatehandler).

To learn how to use this interface, please see [this](../../getting-started/android-sdk/sdk-status-updates.md) guide.

## OnSdkStatusUpdateHandler

|  |  |
| :--- | :--- |
| void | [onSdkStatusUpdate](onsdkstatusupdatehandler.md#onsdkstatusupdate) \(\) |



### `onSdkStatusUpdate`

> ```java
> void onSdkStatusUpdate(SdkStatus status)
> ```
>
> Called whenever the SDK status changes \(or more specifically, whenever one of the fields of [`SdkStatus`](sdkstatus/) changes\).
>
> | Parameters |  |
> | :--- | :--- |
> | status | An [`Sdkstatus`](sdkstatus/) object representing the current SDK status. |

