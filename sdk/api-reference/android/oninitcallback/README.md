# OnInitCallback

This interface is used with [`init(SdkConfig, OnInitCallback)`](../sentiance.md#init).

## OnInitCallback API

|  |  |
| :--- | :--- |
| void | [onInitFailure](./#oninitfailure) \([InitIssue](initissue.md) issue\) |
| void | [onInitSuccess](./#oninitsuccess) \(\) |



### `onInitFailure()`

> ```java
> void onInitFailure(InitIssue issue)
> ```
>
> Called when an issue was encountered while initializing the SDK.
>
> | Parameters |  |
> | :--- | :--- |
> | issue | An [`InitIssue`](initissue.md) enum indicating the issue. |

### `onInitSuccess()`

> ```java
> void onInitSuccess()
> ```
>
> Called when SDK initialization completed successfully. You can now start the SDK detections, and access any of the other methods on the [`Sentiance`](../sentiance.md) class.



