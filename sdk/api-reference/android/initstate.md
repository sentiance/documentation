# InitState

Indicates the SDK initialization state.

| **Attributes** |  |
| :--- | :--- |
| **NOT\_INITIALIZED** | The SDK has not been initialized or a previous initialization attempt has failed. To initialize the SDK, call [`init(SdkConfig, OnInitCallback)`](sentiance.md#init). |
| **INIT\_IN\_PROGRESS** | Initialization is in progress. When it completes, the SDK will call [`onInitSuccess()`](oninitcallback/#oninitsuccess) on success, and [`onInitFailure(InitIssue)`](oninitcallback/#oninitfailure) on failure. Do not call init during this state. Doing so will throw an [`SdkException`](sdkexception.md). |
| **INITIALIZED** | The SDK has been initialized. Do not call init during this state. Doing so will throw an [`SdkException`](sdkexception.md). |
| **RESETTING** | SDK reset is in progress as a result of calling [`reset(ResetCallback)`](sentiance.md#reset). |



