# initWithConfig

This interface is used with [`initWithConfig:(SENTConfig* config) success:^(void)success failure:^(void)failure`](../../android/sentiance.md#init)

### initWithConfig

|  |  |
| :--- | :--- |
| ^\(void\) | [success](../../android/oninitcallback/#oninitsuccess) \(\) |
| ^\(void\) | [failure](../../android/oninitcallback/#oninitfailure) \(SENTInitIssue issue\) |

### `success()`

> ```java
> ^(void)success
> ```
>
> Called when SDK initialization completed successfully. You can now start the SDK detections, and access any of the other methods on the Sentiance class.

### `failure()`

> ```java
> ^(void)failure(SENTInitIssue issue)
> ```
>
> Called when an issue was encountered while initializing the SDK.
>
> | Parameters |  |
> | :--- | :--- |
> | issue | An [`SENTInitIssue`](../../android/oninitcallback/initissue.md) enum indicating the issue. |

