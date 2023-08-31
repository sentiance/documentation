# OnInitCallback

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`init(SdkConfig, OnInitCallback)`](../sentiance.md#init).

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
> Called when SDK initialization completed successfully. You can now start the SDK detections, and access any of the other methods on the [`Sentiance`](../sentiance.md) class.

