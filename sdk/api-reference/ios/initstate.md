# InitState

Indicates the SDK initialization status.

| Attributes | Description |
| :--- | :--- |
| **SENTNotInitialized** | The SDK has not been initialized or a previous initialization attempt has failed. To initialize the SDK, call _\[\[SENTSDK sharedInstance\] initWithConfig:\(SENTConfig \*\) success:^\(void\)success failure:^\(SENTInitIssue issue\)failure\]_ |
| **SENTInitInProgress** | Initialization is in progress. When it completes, the SDK will call success\(\) and failure\(\) if something went wrong. Do not call init during this state. Doing so will throw an exception. |
| **SENTInitialized** | The SDK has been initialized. Do not call init during this state. Doing so will throw an exception. |

