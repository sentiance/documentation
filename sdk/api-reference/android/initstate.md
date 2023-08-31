# InitState

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Indicates the SDK initialization state.

| **NOT\_INITIALIZED**   | The SDK has not been initialized or a previous initialization attempt has failed. To initialize the SDK, call [`init(SdkConfig, OnInitCallback)`](sentiance.md#init).                                                                                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **INIT\_IN\_PROGRESS** | Initialization is in progress. When it completes, the SDK will call [`onInitSuccess()`](oninitcallback/#oninitsuccess) on success, and [`onInitFailure(InitIssue)`](oninitcallback/#oninitfailure) on failure. Do not call init during this state. Doing so will throw an [`SdkException`](sdkexception.md). |
| **INITIALIZED**        | The SDK has been initialized. Do not call init during this state. Doing so will throw an [`SdkException`](sdkexception.md).                                                                                                                                                                                  |
| **RESETTING**          | SDK reset is in progress as a result of calling [`reset(ResetCallback)`](sentiance.md#reset).                                                                                                                                                                                                                |

