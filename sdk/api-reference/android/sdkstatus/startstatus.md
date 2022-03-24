# StartStatus

Represents the detection status of the SDK.

| **NOT\_STARTED**   | SDK detections were not started (i.e. [`start()`](../sentiance.md#start) was never called), or are stopped (by explicitly calling [`stop()`](../sentiance.md#stop)).                                                                                                                                 |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **PENDING**        | The enclosing app requested the start of SDK detections, but it could not be completed (e.g. because the user is not enabled on the Sentiance API, permissions are not granted, or location settings are invalid). When the underlying issues are resolved, the detections will start automatically. |
| **STARTED**        | The SDK detections are successfully started after the enclosing app has called [`start()`](../sentiance.md#start).                                                                                                                                                                                   |
| **START\_EXPIRED** | The SDK start request expired on the date specified when calling [`start(Date, OnStartFinishedhandler)`](../sentiance.md#start-1). Detections are no longer running.                                                                                                                                 |

