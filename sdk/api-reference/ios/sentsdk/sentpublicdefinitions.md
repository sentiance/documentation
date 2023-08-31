# SENTPublicDefinitions

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

### Authentication status items

| **SENTInitIssueInvalidCredentials** | Your app ID and secret could not be used to create a Sentiance user account. Make sure they are correct, and try again.                                   |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SENTInitIssueChangedCredentials** | The app ID and/or secret have changed. The Sentiance SDK does not support changing app credentials. If this was intentional, uninstall the app and retry. |
| **SENTInitIssueServiceUnreachable** | An issue was encountered while trying to reach the Sentiance API. Make sure your internet connection is working and retry.                                |
| **SENTInitIssueLinkFailed**         | An issue was encountered when trying to link the installation ID to the meta-user.                                                                        |
| **SENTInitIssueResetInProgress**    | SDK reset is in progress.                                                                                                                                 |

### Status of the SDK

| **Attributes**                |                                |
| ----------------------------- | ------------------------------ |
| **SENTStartStatusNotStarted** | SDK not started yet            |
| **SENTStartStatusPending**    | SDK initialization in progress |
| **SENTStartStatusStarted**    | SDK has started successfuly    |

### Trip trigger status

| **Attributes**           |                                                              |
| ------------------------ | ------------------------------------------------------------ |
| **SENTTripTypeSDK**      | Trip started by SDK                                          |
| **SENTTripTypeExternal** | Trip start triggered manually by calling \[SENTSDK startTip] |

### Transportation mode detected by Sentiance SDK

| **Attributes**               |   |
| ---------------------------- | - |
| **SENTTransportModeUnknown** |   |
| **SENTTransportModeCar**     |   |
| **SENTTransportModeBicycle** |   |
| **SENTTransportModeOnFoot**  |   |
| **SENTTransportModeTrain**   |   |
| **SENTTransportModeTram**    |   |
| **SENTTransportModeBus**     |   |
| **SENTTransportModePlane**   |   |
| **SENTTransportModeBoat**    |   |
| **SENTTransportModeMetro**   |   |
| **SENTTransportModeRunning** |   |
