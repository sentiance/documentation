# SENTPublicDefinitions

### SENTInitIssue

Initialization failure issues

```objectivec
typedef NS_ENUM(NSUInteger, SENTInitIssue)
```

| Issue                               | Description                                                                            |
| ----------------------------------- | -------------------------------------------------------------------------------------- |
| **SENTInitIssueInvalidCredentials** | Given App ID and Secret pair is invalid                                                |
| **SENTInitIssueChangedCredentials** | Given App ID and Secret pair has been changed                                          |
| **SENTInitIssueServiceUnreachable** | Service unreachable due to network. Most likely due to network or availability issues. |
| **SENTInitIssueLinkFailed**         | User linking failed                                                                    |
| **SENTInitIssueResetInProgress**    | Reset of the SDK is in progress                                                        |



### SENTStartStatus

Defines the status of the SDK

```objectivec
typedef NS_ENUM(NSUInteger, SENTStartStatus)
```

| Issue                         | Description                    |
| ----------------------------- | ------------------------------ |
| **SENTStartStatusNotStarted** | SDK not started yet            |
| **SENTStartStatusPending**    | SDK initialization in progress |
| **SENTStartStatusStarted**    | SDK has started successfuly    |
| **SENTStartStatusExpired**    | SDK has been expired           |





### SENTTransportMode

Current Transportation mode detected by Sentiance SDK

```objectivec
typedef NS_ENUM(NSUInteger, SENTTransportMode)
{
    SENTTransportModeUnknown = 1,
    SENTTransportModeCar     = 2,
    SENTTransportModeBicycle = 3,
    SENTTransportModeOnFoot  = 4,
    SENTTransportModeTrain   = 5,
    SENTTransportModeTram    = 6,
    SENTTransportModeBus     = 7,
    SENTTransportModePlane   = 8,
    SENTTransportModeBoat    = 9,
    SENTTransportModeMetro   = 10,
    SENTTransportModeRunning = 11
};
```

###

### SENTExternalEventType

Deprecated.

External event type definition for SDK trigger





### SENTripType

Trip trigger status

```objectivec
typedef NS_ENUM(NSUInteger, SENTTripType)
{
    SENTTripTypeSDK      = 1,
    SENTTripTypeExternal = 2
};
```

| Trip Type            | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| SENTTripTypeSDK      | Trip started by SDK.                                         |
| SENTTripTypeExternal | Trip start triggered manually by calling \[SENTSDK startTip] |



### SENTInitializationFailureReason

Initialization failure Issues returned during Initialization

```objectivec
typedef NS_ENUM(NSUInteger, SENTInitializationFailureReason) {
    SENTInitializationFailureReasonNone,
    SENTInitializationFailureReasonUnsupportedOSVersion,
    /** Reinitialization is allowed only immediately after resetting the SDK (i.e. before creating a user). */
    SENTInitializationFailureReasonReinitializationNotAllowed,
    SENTInitializationFailureReasonSdkResetInProgress,
    SENTInitializationFailureReasonInternalInconsistency,
};
```

