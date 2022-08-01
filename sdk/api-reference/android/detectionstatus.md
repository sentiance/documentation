---
description: Represents the detection status of the SDK.
---

# DetectionStatus

### **`DISABLED`**

Detections are disabled. Call enableDetections() to enable them.

### **`EXPIRED`**

Detections were disabled automatically, as per the expiration date that was provided when calling enableDetections(Date).

### **`ENABLED_BUT_BLOCKED`**

Detections are enabled, but not running. Check getSdkStatus() to find out why.

Possible reasons can be:

* Remotely disabled user.
* Insufficient permissions.
* Invalid device location settings.

### **`ENABLED_AND_DETECTING`**

Detections are enabled and running.

