---
description: The SENTSDK class is the main entry point for interacting with the SDK.
---

# SENTSDK

### sharedInstance

Method to call the shared instance of the SDK.

```objectivec
+ (instancetype) sharedInstance;
```

### initWithConfig: success: failure:

SDK intialization method. It sets up the modules internally and handles user authentication.

```objectivec
- (void) initWithConfig: (SENTConfig *) config 
                success: (void (^)(void)) success 
                failure: (void (^)(SENTInitIssue issue)) failure;
```

| Parameter |  |
| :--- | :--- |
| config | The configuration used to authenticate the user. |
| success | The success block called when init succeeded. |
| failure | The failure block called when init failed. It takes a SENTInitIssue issue indicating the reason of the failure. |

{% hint style="warning" %}
Init should only be called once, unless initialisation fails.
{% endhint %}

### start:

Start the SDK.

```objectivec
- (void) start: (void (^)(SENTSDKStatus* status)) completion;
```

| Parameter |  |
| :--- | :--- |
| completion | The completion block called when the SDK has started. SENTSDKStatus object indicates any issue that occured when the SDK started. |

{% hint style="info" %}
start should be called only after the SDK has been successfully initialised.
{% endhint %}

### stop

Stop the SDK.

```objectivec
- (void) stop;
```

### getUserId

Returns the user ID

```objectivec
- (NSString *) getUserId;
```

### getUserAccessToken:

Returns the users Access Token if the user is authenticated

```objectivec
- (void) getUserAccessToken: (void (^)(NSString *token)) success 
                    failure: (void (^)(void)) failure;
```

### addUserMetadataField: value:

Interface method to set metadata for user. Metadata is any additional data that enclosing app is willing to set for this user/app combination This metadata could contain vital information related to procesing wrt to the enclosing app.

```objectivec
- (void) addUserMetadataField: (NSString*) label 
                        value: (NSString*) value;
```

| Parameter |  |
| :--- | :--- |
| label | Field name for the new entry. |
| value | Value for the new entry. |

### addUserMetadataFields:

Interface method to set metadata for user. Metadata is any additional data that enclosing app is willing to set for this user/app combination This metadata could contain vital information related to procesing wrt to the enclosing app.

```objectivec
- (void) addUserMetadataFields: (NSDictionary *) metadata;
```

| Parameter |  |
| :--- | :--- |
| metadata | Key value pair data from enclosing app, could have any structure as long as it can be contained in a dictionary. |

### removeUserMetadataField:

Method to remove user data field to the sdk metadata \(locally as well as on backend\).

```text
- (void) removeUserMetadataField:(NSString*)label;
```

| Parameter |  |
| :--- | :--- |
| label | Field name for the new entry. |

### addTripMetadata:

add metadata pertaining to the ongoing external trip. All added metadata will be aggregated and added to the trip payload. Returns NO if there's no ongoing external trip.

```objectivec
- (BOOL)addTripMetadata:(NSDictionary *)metadata;
```

| Parameter |  |
| :--- | :--- |
| metadata | key value pair data from enclosing app, could have any structure as long as it can be contained in a dictionary. The only time we return NO is when a trip is not ongoing, metadata contains NSNull objects or nil itself. |

### startTrip: transportModeHint: success: failure:

Start a Trip manually

```objectivec
- (void) startTrip: (NSDictionary*) metadata 
 transportModeHint: (SENTTransportMode) mode 
           success: (void (^)(void)) success 
           failure: (void (^)(SENTSDKStatus* status)) failure;
```

| Parameter |  |
| :--- | :--- |
| metadata | Key value pair data from enclosing app, could have any structure as long as it can be contained in a dictionary. |
| transportModeHint | Suggest of transport mode  |

### stopTrip: failure:

Stop a trip.

```objectivec
- (void) stopTrip: (void (^)(void)) success 
          failure: (void (^)(SENTSDKStatus* status)) failure;
```

### setTripTimeOutListener:

Set a trip timeout block. 

```objectivec
- (void) setTripTimeOutListener: (void (^)(void)) tripDidTimeOut;
```

{% hint style="info" %}
**tripDidTimeOut** block will be called each time trip will time out
{% endhint %}

### setCrashListener:

Set vehicle crash detection block. 

```objectivec
- (void)setCrashListener:(void (^)(NSDate *date, CLLocation *lastKnownLocation))crashCallback;
```

### setUserActivityListener:

This method provides the enclosing app the ability to get SDK detection updates. So when the SDK is in a trip or a stationary, it informs the app via a callback, providing some extra information.

```objectivec
- (void)setUserActivityListerner:(void (^)(SENTUserActivity *userActivity))onChange;
```

### getUserActivity

This method provides the enclosing app the ability to get SDK current user activity state. It is a trip or stationary with some enriched information.

```objectivec
- (SENTUserActivity *)getUserActivity;
```

### isTripOngoing:

Interface method to check if trip is in progress or not.

```objectivec
- (BOOL) isTripOngoing: (SENTTripType) tripType;
```

| Parameter |  |
| :--- | :--- |
| tripType | Type of ongoing trip, _SDK_ - started by SDK, _External_ - started by the application |

### submitDetections: failure:

Submits all the pending detections to backend, without considering any quota related updates and returns the status of these submissions via a callback to the enclosing app.

```objectivec
- (void) submitDetections: (void (^)(void)) success 
                  failure: (void (^)(void)) failure;
```

| Parameter |  |
| :--- | :--- |
| success | Success block which is to be called when forced submission completes. |
| failure | Failure block which is to be called when forced submission completes. |

### isInitialised

{% hint style="warning" %}
This method is deprecated. Please use -\(SENTSDKInitState\)getInitState;
{% endhint %}

Return state of inialization of the SDK: SENTNotInitialized, SENTInitInProgress, SENTInitialized

```objectivec
- (BOOL) isInitialised;
```

### getInitState

Return state of inialization of the SDK: **SENTNotInitialized**, **SENTInitInProgress**, **SENTInitialized**

```objectivec
- (SENTSDKInitState) getInitState;
```

### getSdkStatus

Get SDK status information

```objectivec
- (SENTSDKStatus*) getSdkStatus;
```

### getVersion

Get SDK version

```objectivec
- (NSString *) getVersion;
```

### getWifiQuotaLimit

Get SDK WiFi quota limit

```objectivec
- (long) getWifiQuotaLimit;
```

### getWiFiQuotaUsage

Get SDK WiFi quota usage

```objectivec
- (long) getWiFiQuotaUsage;
```

### getMobileQuotaLimit

Get SDK mobile data quota limit

```objectivec
- (long) getMobileQuotaLimit;
```

### getMobileQuotaUsage

Get SDK mobile data quota usage

```objectivec
- (long) getMobileQuotaUsage;
```

### getDiskQuotaLimit

Get SDK disk quota limit

```objectivec
- (long) getDiskQuotaLimit;
```

### getDiskQuotaUsage

Get SDK disk quota usage

```objectivec
- (long) getDiskQuotaUsage;
```

