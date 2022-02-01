# ResetCallback

This interface is used with [`reset(ResetCallback)`](../sentiance.md#reset).

## ResetCallback API

|  |  |
| :--- | :--- |
| void | [onResetFailure](./#onresetfailure) \([ResetFailureReason](resetfailurereason.md) reason\) |
| void | [onResetSuccess](./#onresetsuccess) \(\) |



### `onResetFailure()`

> ```java
> void onResetFailure(ResetFailureReason reason)
> ```
>
> Called when the SDK reset fails.
>
> | Parameters |  |
> | :--- | :--- |
> | reason | A [`ResetFailureReason`](resetfailurereason.md) enum indicating the failure reason. |

### `onResetSuccess()`

> ```java
> void onResetSuccess()
> ```
>
> Called when the SDK reset completes.

