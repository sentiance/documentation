# StartTripFailureReason

Represents the failure reason.

| **NO\_USER**                 | No Sentiance user is present on device. Call [Sentiance#createUser(UserCreationOptions)](../sentiance.md.md#createuser) to create a user.      |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **DETECTIONS\_DISABLED**     | Detections are disabled. Enable them first before starting a trip. See [`Sentiance#enableDetections()`](../sentiance.md.md#enabledetections)`` |
| **DETECTIONS\_BLOCKED**      | Detections are enabled but not running. Check the SDK's status to find out why. see [`StartTripError#getSdkStatus()`](./#getsdkstatus)``       |
| **TRIP\_ALREADY\_STARTED**   | An external trip is already started. To start a new trip, call [`Sentiance#stopTrip()`](../sentiance.md.md#stoptrip)  first.                   |
| **USER\_DISABLED\_REMOTELY** | The user is disabled remotely.                                                                                                                 |

