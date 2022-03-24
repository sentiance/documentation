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

SDK initialization method. It sets up the modules internally and handles user authentication.

```objectivec
- (void) initWithConfig: (SENTConfig *) config 
                success: (void (^)(void)) success 
                failure: (void (^)(SENTInitIssue issue)) failure;
```

| Parameter |                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------- |
| config    | The configuration used to authenticate the user.                                                                |
| success   | The success block called when init succeeded.                                                                   |
| failure   | The failure block called when init failed. It takes a SENTInitIssue issue indicating the reason of the failure. |

{% hint style="warning" %}
Init should only be called once, unless initialization fails.
{% endhint %}

### start:

Start the SDK.

```objectivec
- (void) start: (void (^)(SENTSDKStatus* status)) completion;
```

| Callback       |                                                                                                                                                        |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **completion** | The completion block called when the SDK has started. [SENTSDKStatus](sentsdkstatus.md) object indicates any issue that occurred when the SDK started. |

{% hint style="info" %}
start should be called only after the SDK has been successfully initialized.
{% endhint %}

### startWithStopDate:

Start the SDK with expiration date.

```objectivec
- (void)startWithStopDate:(NSDate *)sdkStopDate 
               completion:(void (^)(SENTSDKStatus *status))completion;
```

| Parameter       |                                                                                                                            |
| --------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **sdkStopDate** | Should be set with date in the future. Dates in past will cause imediate stop of SDK. Setting nil will start SDK as usual. |

| Callback       |                                                                                                                                                        |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **completion** | The completion block called when the SDK has started. [SENTSDKStatus](sentsdkstatus.md) object indicates any issue that occurred when the SDK started. |

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

| Parameter |                               |
| --------- | ----------------------------- |
| label     | Field name for the new entry. |
| value     | Value for the new entry.      |

### addUserMetadataFields:

Interface method to set metadata for user. Metadata is any additional data that enclosing app is willing to set for this user/app combination This metadata could contain vital information related to processing wrt to the enclosing app.

```objectivec
- (void) addUserMetadataFields: (NSDictionary *) metadata;
```

| Parameter |                                                                                                                  |
| --------- | ---------------------------------------------------------------------------------------------------------------- |
| metadata  | Key value pair data from enclosing app, could have any structure as long as it can be contained in a dictionary. |

### removeUserMetadataField:

Method to remove user data field to the sdk metadata (locally as well as on backend).

```
- (void) removeUserMetadataField:(NSString*)label;
```

| Parameter |                               |
| --------- | ----------------------------- |
| label     | Field name for the new entry. |

### addTripMetadata:

add metadata pertaining to the ongoing external trip. All added metadata will be aggregated and added to the trip payload. Returns NO if there's no ongoing external trip.

```objectivec
- (BOOL)addTripMetadata:(NSDictionary *)metadata;
```

| Parameter |                                                                                                                                                                                                                            |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| metadata  | key value pair data from enclosing app, could have any structure as long as it can be contained in a dictionary. The only time we return NO is when a trip is not ongoing, metadata contains NSNull objects or nil itself. |

### startTrip: transportModeHint: success: failure:

Start a Trip manually

```objectivec
- (void) startTrip: (NSDictionary*) metadata 
 transportModeHint: (SENTTransportMode) mode 
           success: (void (^)(void)) success 
           failure: (void (^)(SENTSDKStatus* status)) failure;
```

| Parameter         |                                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------- |
| metadata          | Key value pair data from enclosing app, could have any structure as long as it can be contained in a dictionary. |
| transportModeHint | Suggest of transport mode                                                                                        |

### stopTrip: failure:

Stop a trip.

```objectivec
- (void) stopTrip: (void (^)(void)) success 
          failure: (void (^)(SENTSDKStatus* status)) failure;
```

### setTripTimeOutListener:

Set a trip timeout block.&#x20;

```objectivec
- (void) setTripTimeOutListener: (void (^)(void)) tripDidTimeOut;
```

{% hint style="info" %}
**tripDidTimeOut** block will be called each time trip will time out
{% endhint %}

### isVehicleCrashDetectionSupported:

Checks if vehicle crash detection is supported on the device for the specified trip type.

&#x20;The result depends on multiple criteria, such as if vehicle crash detection is enabled for your app, and if the necessary sensors are present on the device.

```objectivec
- (BOOL)isVehicleCrashDetectionSupported:(SENTTripType)tripType;
```

| Parameter |                                              |
| --------- | -------------------------------------------- |
| tripType  | The type of trip for which you want to check |

### invokeDummyVehicleCrash

Invokes a dummy vehicle crash event. Use this method to test your vehicle crash detection integration.

Calling this method will invoke the handler from [`setVehicleCrashHandler:`](./#setvehiclecrashhandler)or [`setCrashListener:`](./#setcrashlistener)depending on which handler was set last.

```objectivec
- (void)invokeDummyVehicleCrash;
```

{% hint style="info" %}
This method is intended for testing your integration, and not for production use.
{% endhint %}

### setCrashListener:

{% hint style="warning" %}
**Deprecated**

[`setCrashListener:`](./#setcrashlistener) is deprecated. Use [`setVehicleCrashHandler:`](./#setvehiclecrashhandler) instead.
{% endhint %}

Set vehicle crash detection block.&#x20;

```objectivec
- (void)setCrashListener:(void (^)(NSDate *date, CLLocation *lastKnownLocation))crashCallback;
```

### setVehicleCrashHandler:

Sets a handler that is invoked when a vehicle crash is detected with an instance of [`SENTVehicleCrashEvent`](../sentvehiclecrashevent.md).

```objectivec
- (void)setVehicleCrashHandler:(void (^)(SENTVehicleCrashEvent *crashEvent))vehicleCrashHandler;
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

| Parameter |                                                                                       |
| --------- | ------------------------------------------------------------------------------------- |
| tripType  | Type of ongoing trip, _SDK_ - started by SDK, _External_ - started by the application |

### submitDetections: failure:

Submits all the pending detections to backend, without considering any quota related updates and returns the status of these submissions via a callback to the enclosing app.

```objectivec
- (void) submitDetections: (void (^)(void)) success 
                  failure: (void (^)(void)) failure;
```

| Parameter |                                                                       |
| --------- | --------------------------------------------------------------------- |
| success   | Success block which is to be called when forced submission completes. |
| failure   | Failure block which is to be called when forced submission completes. |

### isInitialised

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Please use [`-(SENTSDKInitState)getInitState`](./#getinitstate) `instead.`
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

### reset: failure:

{% hint style="info" %}
The reset functionality is intended for removing all data in the device to handle a case such as a user logging out from an app or user requesting data deletion in the local app. It should not be used to reset the internal state of the SDK.
{% endhint %}

Resets the Sentiance SDK. Calling this method results in stopping of all SDK operations and deleting all SDK user data from the device. Additionally, the SDK will be uninitialized, allowing reinitialization and new Sentiance user creation.

The reset operation may take a while, in which case the SDK's initialization state will be set to [InitState](sentsdkstatus.md#sentsdkinitstate) **SENTResetting** until it's complete. Calling any other SDK method during this time will either be ignored or return a default value.&#x20;

Note that calling this method during intermediate initialization states (i.e. [InitState ](sentsdkstatus.md#sentsdkinitstate)**SENTInitInProgress**} and [InitState](sentsdkstatus.md#sentsdkinitstate) **SENTResetting** will fail.

```objectivec
- (void)reset:(void(^)(void))success failure:(void(^)(SENTResetFailureReason reason))failure;
```

| Parameter |                                                                                                              |
| --------- | ------------------------------------------------------------------------------------------------------------ |
| success   | Success block callback when reset successfully done                                                          |
| failure   | Failure callback when with one of [SENTResetFailureReason](sentsdkstatus.md#sentresetfailurereason) happened |

### setTripProfileHandler:

{% hint style="warning" %}
**Deprecated**

This method was deprecated in v5.12.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

Sets a block to execute after a trip finishes and is profiled on device. The profiling data is returned with a [SENTTripProcessingTripProfile](../tripprofile-1/) object.&#x20;

Each [SENTTripProcessingTripProfile](../tripprofile-1/) contains multiple transport segments which each is assigned a [SENTTripProcessingVehicleMode](../tripprofile-1/vehiclemode-1.md). The handler makes sure that only the transport segments that is assigned [SENTTripProcessingVehicleModeVehicle](../tripprofile-1/vehiclemode-1.md) are returned.&#x20;

{% hint style="info" %}
In order to use this handler, your app configuration must enable the trip profiling feature explicitly. Full trip profiling also needs to be disabled from the SDK. Please see [`[SENTSDK setFullTripProfilingEnabled:]`](./#setfulltripprofilingenabled) for more details.
{% endhint %}

```objectivec
- (void)setTripProfileHandler:(void (^) (SENTTripProcessingTripProfile *tripProfile))tripProfileHandler;
```

| Parameter          |                                                                       |
| ------------------ | --------------------------------------------------------------------- |
| tripProfileHandler | The block to execute after a trip finishes and is profiled on device. |

### setFullTripProfilingEnabled:

{% hint style="warning" %}
**Deprecated**

This method was deprecated in v5.12.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

Changes the trip profiling mode the SDK is currently using.

Pass YES to let the trips being profiled on the Sentiance platform. If you previously set an on-device trip profiling handler via [`[SENTSDK setTripProfileHandler:]`](./#settripprofilehandler), this also disables that handler. When NO is passed later, the handler continues to be called.

Pass NO to enable on-device trip profiling without uploading trip information to the Sentiance platform.

{% hint style="info" %}
In order to use this method, your app configuration must enable the trip profiling feature explicitly.&#x20;
{% endhint %}

```objectivec
- (void)setFullTripProfilingEnabled:(BOOL)enabled;
```

| Parameter |                                                                                  |
| --------- | -------------------------------------------------------------------------------- |
| enabled   | The flag that enables or disables trips being profiled on the Sentiance platform |

### setSpeedLimit:

{% hint style="warning" %}
**Deprecated**

This method was deprecated in v5.12.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

Sets a custom speed limit in m/s that will be used during on-device speeding estimation. Any value that is less than or equal to "0" will be ignored.

If a custom speed limit is not set, the SDK uses a value of 23 m/s as the default speed limit.

{% hint style="info" %}
In order to use this method, your app configuration must enable the trip profiling feature explicitly.&#x20;
{% endhint %}

```objectivec
- (void)setSpeedLimit:(double)speedLimit;
```

| Parameter  |                                                                              |
| ---------- | ---------------------------------------------------------------------------- |
| speedLimit | The speed limit value that will be used during on-device speeding estimation |
