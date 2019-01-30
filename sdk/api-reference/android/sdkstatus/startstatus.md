# StartStatus

Represents the detection status of the SDK.

| **Attributes** |  |
| :--- | :--- |
| **NOT\_STARTED** | SDK detections were not started, or are stopped. |
| **PENDING** | The enclosing app requested the start of SDK detections, but it could not be completed \(e.g. because the user is not enabled on the Sentiance API, permissions are not granted, or location settings are invalid\). When the underlying issues are resolved, the detections will start automatically. |
| **STARTED** | The SDK detections are successfully started after the enclosing app has called [`start()`](../sentiance.md#start). |

