# SENTSDKStatus

### SENTSDKInitState

Indicates the SDK initialization status.

| **SENTNotInitialized** | The SDK has not been initialized or a previous initialization attempt has failed. To initialize the SDK, call _`[[SENTSDK sharedInstance] initWithConfig:(SENTConfig *) success:^(void)success failure:^(SENTInitIssue issue)failure]`_ |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SENTInitInProgress** | Initialization is in progress. When it completes, the SDK will call success() and failure() if something went wrong.                                                                                                                    |
| **SENTInitialized**    | The SDK has been initialized.                                                                                                                                                                                                           |
| **SENTResetting**      | The SDK reset is in progress. All public method calls will be ignored and callbacks will not be triggered during this state.                                                                                                            |

### SENTQuotaStatus

Quota status applicable to disk and network usage.

| Attributes                  | Description                                    |
| --------------------------- | ---------------------------------------------- |
| **SENTQuotaStatusOK**       | The quota is below the threshold.              |
| **SENTQuotaStatusWarning**  | More than 90 percent of the quota is consumed. |
| **SENTQuotaStatusExceeded** | The quota is fully consumed.                   |

### SENTResetFailureReason

Indicates the failure reason of the latest reset attempt.

| Type                                     | Description                        |
| ---------------------------------------- | ---------------------------------- |
| **SENTResetFailureReasonInitInProgress** | SDK initialization is in progress. |
| **SENTResetFailureReasonResetting**      | Another SDK reset is in progress.  |

### canDetect

True only if detections are possible (i.e. there are no issues blocking detection)

```objectivec
@property(nonatomic, assign) BOOL canDetect;
```

### isRemoteEnabled

True if kill-switch is not enabled

```objectivec
@property(nonatomic, assign) BOOL isLocationPermGranted;
```

### locationPermission

CanDetect is true, if conditions for the location permissions are met.

```objectivec
@property (nonatomic, assign) SENTLocationPermission locationPermission;
```

### isAccelPresent

True if device has an accelerometer

```objectivec
@property(nonatomic, assign) BOOL isAccelPresent;
```



### isPreciseLocationAuthorizationGranted

True if location accuracy authorization permission is granted. If false, canDetect will be false.

```objectivec
@property (nonatomic, assign) BOOL isPreciseLocationAuthorizationGranted;
```



### isGyroPresent

True if device has a gyroscope

```objectivec
@property(nonatomic, assign) BOOL isGyroPresent;
```

### isGpsPresent

True if device has a GPS unit

```objectivec
@property(nonatomic, assign) BOOL isGpsPresent;
```

### wifiQuotaStatus

Indicates WiFi quota state.

Sentiance assigns a limited quota for the SDK to utilized over a period of 1 month. The quota usage is reset on the first day of each month. Once the quota is exceeded, data submission over WiFi stops. The default quota is 2048 MB, but is configurable by Sentiance.

```objectivec
@property(nonatomic, assign) SENTQuotaStatus wifiQuotaStatus;
```

### mobileQuotaStatus

Indicates mobile data quota state.

Sentiance assigns a limited quota for the SDK to utilized over a period of 1 month. The quota usage is reset on the first day of each month. Once the quota is exceeded, data submission over mobile data stops. The default quota is 250 MB, but is configurable by Sentiance.

```objectivec
@property(nonatomic, assign) SENTQuotaStatus mobileQuotaStatus;
```

### diskQuotaStatus

Indicates disk quota state.

Sentiance assigns a limited quota for the SDK to utilized. Once the quota is exceeded, SDK detections stop. The default quota is 128 MB, but is configurable by Sentiance.

```objectivec
@property(nonatomic, assign) SENTQuotaStatus diskQuotaStatus;
```

### userExists

True if a user exists on the device.

```objectivec
@property (nonatomic, assign) BOOL userExists;
```

### detectionStatus

Indicates whenever the detection is enabled and start or the status of the SDK.

```objectivec
@property (nonatomic, readonly) SENTDetectionStatus detectionStatus;
```

### backgroundRefreshStatus

Get background refresh status for the background processing and fetch capabilities.

```objectivec
@property (nonatomic, assign, readonly) UIBackgroundRefreshStatus backgroundRefreshStatus;
```

### startStatus

Indicates the status of the SDK

```objectivec
@property(nonatomic, assign) SENTStartStatus startStatus;
```

| Attributes                    | Description                                                                                                                                                                                                                                                                                          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SENTStartStatusNotStarted** | SDK detections were not started (i.e. start: was never called), or are stopped (by explicitly calling [stop](sentiance.md#stop)).                                                                                                                                                                    |
| **SENTStartStatusPending**    | The enclosing app requested the start of SDK detections, but it could not be completed (e.g. because the user is not enabled on the Sentiance API, permissions are not granted, or location settings are invalid). When the underlying issues are resolved, the detections will start automatically. |
| **SENTStartStatusStarted**    | The SDK detections are successfully started after the enclosing app has called [start:](sentiance.md#start)                                                                                                                                                                                          |
| **SENTStartStatusExpired**    | The SDK start request expired on the date specified when calling [startWithStopDate](sentiance.md#startwithstopdate). Detections are no longer running.                                                                                                                                              |

### isEqualToSDKStatus

Returns a Boolean value that indicates whether a given [SDKStatus](sentsdkstatus.md) is equal to the receiver using item by item comparsion.

```objectivec
- (BOOL) isEqualToSDKStatus: (SENTSDKStatus*) sdkStatus;
```

