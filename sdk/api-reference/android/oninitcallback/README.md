# OnInitCallback

This interface is used with [`init(SdkConfig, OnInitCallback)`](broken-reference).

## OnInitCallback API

### `onInitFailure()`

> ```java
> void onInitFailure(InitIssue issue, @Nullable Throwable throwable)
> ```
>
> Called when an issue was encountered while initializing the SDK.

| Parameters |                                                                                                                                           |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| issue      | An [`InitIssue`](initissue.md) enum indicating the issue.                                                                                 |
| throwable  | An optional [`Throwable`](https://developer.android.com/reference/java/lang/Throwable) in case of [`INITIALIZATION_ERROR`](initissue.md). |

### `onInitSuccess()`

> ```java
> void onInitSuccess()
> ```
>
> Called when SDK initialization completed successfully. You can now start the SDK detections, and access any of the other methods on the [`Sentiance`](broken-reference) class.

