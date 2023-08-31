# ResetCallback

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`reset(ResetCallback)`](../sentiance.md#reset).

## ResetCallback API

### `onResetFailure()`

> ```java
> void onResetFailure(ResetFailureReason reason)
> ```
>
> Called when the SDK reset fails.

| Parameters |                                                                                     |
| ---------- | ----------------------------------------------------------------------------------- |
| reason     | A [`ResetFailureReason`](resetfailurereason.md) enum indicating the failure reason. |

### `onResetSuccess()`

> ```java
> void onResetSuccess()
> ```
>
> Called when the SDK reset completes.
