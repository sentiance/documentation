# SENTSDKStatus

### SENTSDKInitState

Indicates the SDK initialization status.

| Attributes | Description |
| :--- | :--- |
| **SENTNotInitialized** | The SDK has not been initialized or a previous initialization attempt has failed. To initialize the SDK, call _`[[SENTSDK sharedInstance] initWithConfig:(SENTConfig *) success:^(void)success failure:^(SENTInitIssue issue)failure]`_ |
| **SENTInitInProgress** | Initialization is in progress. When it completes, the SDK will call success\(\) and failure\(\) if something went wrong. Do not call init during this state. Doing so will throw an exception. |
| **SENTInitialized** | The SDK has been initialized. Do not call init during this state. Doing so will throw an exception. |
| **SENTResetting** | The SDK reset is in progress. All public method calls will be ignored and callbacks will not be triggered during this state.  |

### SENTQuotaStatus

Quota status applicable to disk and network usage.

| Attributes | Description |
| :--- | :--- |
| **SENTQuotaStatusOK** | The quota is below the threshold. |
| **SENTQuotaStatusWarning** | More than 90 percent of the quota is consumed. |
| **SENTQuotaStatusExceeded** | The quota is fully consumed. |

### SENTResetFailureReason

Indicates the failure reason of the latest reset attempt.

| Attributes | Description |
| :--- | :--- |
| **SENTResetFailureReasonInitInProgress** | SDK initialization is in progress. |
| **SENTResetFailureReasonResetting** | Another SDK reset is in progress. |

### canDetect

True only if detections are possible \(i.e. there are no issues blocking detection\)

```objectivec
@property(nonatomic, assign) BOOL canDetect;
```

### isRemoteEnabled

True if kill-switch is not enabled

```objectivec
@property(nonatomic, assign) BOOL isLocationPermGranted;
```

### isLocationPermGranted

True if location permissions are granted. If false, canDetect will be false.

```objectivec
@property(nonatomic, assign) BOOL isLocationPermGranted;
```

### isBgAccessPermGranted

True if SDK is allowed to run in the background \(iOS\)

```objectivec
@property(nonatomic, assign) BOOL isBgAccessPermGranted;
```

### isAccelPresent

True if device has an accelerometer

```objectivec
@property(nonatomic, assign) BOOL isAccelPresent;
```

### isGyroPresent

True if device has a gyroscope

```objectivec
@property(nonatomic, assign) BOOL isGyroPresent;
```

### isGpsPresent

True if device has a GPS unit

```text
@property(nonatomic, assign) BOOL isGpsPresent;
```

### wifiQuotaStatus

Indicates WiFi quota state

```objectivec
@property(nonatomic, assign) SENTQuotaStatus wifiQuotaStatus;
```

### mobileQuotaStatus

Indicates mobile data quota state

```objectivec
@property(nonatomic, assign) SENTQuotaStatus mobileQuotaStatus;
```

### diskQuotaStatus

Indicates disk quota state

```text
@property(nonatomic, assign) SENTQuotaStatus diskQuotaStatus;
```

### startStatus

Indicates the status of the SDK

```objectivec
@property(nonatomic, assign) SENTStartStatus startStatus;
```

| Attributes | Description |
| :--- | :--- |
| **SENTStartStatusNotStarted** | SDK detections were not started \(i.e. start: was never called\), or are stopped \(by explicitly calling [stop](./#stop)\). |
| **SENTStartStatusPending** | The enclosing app requested the start of SDK detections, but it could not be completed \(e.g. because the user is not enabled on the Sentiance API, permissions are not granted, or location settings are invalid\). When the underlying issues are resolved, the detections will start automatically. |
| **SENTStartStatusStarted** | The SDK detections are successfully started after the enclosing app has called [start:](./#start) |
| **SENTStartStatusExpired** | The SDK start request expired on the date specified when calling [startWithStopDate](./#startwithstopdate). Detections are no longer running. |

### isEqualToSDKStatus

Returns a Boolean value that indicates whether a given [SDKStatus](sentsdkstatus.md) is equal to the receiver using item by item comparsion.

```objectivec
- (BOOL) isEqualToSDKStatus: (SENTSDKStatus*) sdkStatus;
```



