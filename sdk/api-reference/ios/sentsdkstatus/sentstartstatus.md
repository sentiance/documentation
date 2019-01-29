# SENTStartStatus

Represents the detection status of the SDK.

| **Attributes** |  |
| :--- | :--- |
| **SENTStartStatusNotStarted** | SDK detections were not started, or are stopped. |
| **SENTStartStatusPending** | The enclosing app requested the start of SDK detections, but it could not be completed \(e.g. because the user is not enabled on the Sentiance API, permissions are not granted, or location settings are invalid\). When the underlying issues are resolved, the detections will start automatically. |
| **SENTStartStatusStarted** | The SDK detections are successfully started. |



