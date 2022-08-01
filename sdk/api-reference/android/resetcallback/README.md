# ResetCallback

This interface is used with [`reset(ResetCallback)`](../sentiance.md.md#reset-resetcallback).

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
