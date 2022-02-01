# UserActivityType

Represents the type of a detected activity.

| **Attributes** |  |
| :--- | :--- |
| **TRIP** | The SDK detected the user is in a trip. |
| **STATIONARY** | The SDK detected the user is in a stationary state. |
| **UNKNOWN** | A non-active state. This state is set when internal SDK modules are still initializing or starting. It can also be set for other external reasons, such as the device location setting is turned off, location permission not granted to the app, or the SDK is not receiving accurate location fixes. |

