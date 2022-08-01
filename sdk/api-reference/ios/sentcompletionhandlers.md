# SENTCompletionHandlers

### SENTStartTripFailureReason

Failure Issues when Starting a trip manually.

| Issue                                          | Description                                                                     |
| ---------------------------------------------- | ------------------------------------------------------------------------------- |
| SENTStartTripFailureReasonNoUser               | No Sentiance user is present on device.                                         |
| SENTStartTripFailureReasonDetectionsDisabled   | Detections are disabled. Enable them first before starting a trip.              |
| SENTStartTripFailureReasonDetectionsBlocked    | Detections are enabled but not running. Check the SDK's status to find out why. |
| SENTStartTripFailureReasonTripAlreadyStarted   | An external trip is already started.                                            |
| SENTStartTripFailureReasonUserDisabledRemotely | The user is disabled remotely.                                                  |



### SENTSubmitDetectionsFailureReason

Failure issues when submitting detections manually.



| Issue                                                 | Description                             |
| ----------------------------------------------------- | --------------------------------------- |
| SENTSubmitDetectionsFailureReasonNoUser               | No Sentiance user is present on device. |
| SENTSubmitDetectionsFailureReasonNetworkError         | A network error occurred.               |
| SENTSubmitDetectionsFailureReasonUserDisabledRemotely | The user is disabled remotely.          |



### SENTUserAccessTokenFailureReason

Failure issues when requesting user access token.

| Issue                                                | Description                                                                                                                                            |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SENTUserAccessTokenFailureReasonNoUser               | No Sentiance user is present on device. Call createUserWithOptions:completionHandler: to create a user.                                                |
| SENTUserAccessTokenFailureReasonNetworkError         | A network error occurred. This can happen when the existing token is expired, and it was not possible to contact the Sentiance platform to refresh it. |
| SENTUserAccessTokenFailureReasonUserDisabledRemotely | The user is disabled remotely.                                                                                                                         |
