---
description: The Sentiance class is the main entry point for interacting with the SDK.
---

# Sentiance

### shared

The Singleton instance to get the shared instance of the SDK.&#x20;

Usage: Sentiance.shared

```objectivec
+ (instancetype) shared;
```

### sdkStatus

Get SDK status information

```objectivec
@property (nonatomic, readonly) SENTSDKStatus *sdkStatus;
```

### initState

Return state of initialisation of the SDK: SENTNotInitialized, SENTInitInProgress, SENTInitialized.

```objectivec
@property (nonatomic, readonly) SENTSDKInitState initState;
```

### detectionStatus

Get current detection status.

```objectivec
@property (nonatomic, readonly) SENTDetectionStatus detectionStatus;
```

### userActivity

SDK current user activity state. It is a trip or stationary with some enriched information.

```objectivec
@property (nonatomic, readonly) SENTUserActivity * userActivity;
```

### criteriaMaskForUserContextUpdates

{% hint style="info" %}
This method is part of an [Early Access](../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

The criteria for which the delegate property `userContextDelegate` will get invoked.

```objectivec
@property (nonatomic, assign) SENTUserContextUpdateCriteria criteriaMaskForUserContextUpdates;
```

### userContextDelegate

{% hint style="info" %}
This method is part of an [Early Access](../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Delegate property which gets notified when the userContext is updated

```objectivec
@property (nonatomic, weak) id<SENTUserContextDelegate> _Nullable userContextDelegate
```

### version

SDK Version property

```objectivec
@property (nonatomic, readonly) NSString * version;
```

### userId

Returns the user ID.

```objectivec
@property (nonatomic, readonly, nullable) NSString * userId;
```

### userExists

Checks if a Sentiance user exists on the device. You may call this method without having initialized the SDK. Returns true if a Sentiance user exists.

```objectivec
@property (nonatomic, readonly) BOOL userExists;
```

### isUserLinked

Checks if a Sentiance user exists on the device, and whether it is linked to your app's user. You may call this method without having initialized the SDK. Returns true if a Sentiance user exists and is linked.

```objectivec
@property (nonatomic, readonly) BOOL isUserLinked;
```

### isVehicleCrashDetectionSupported

Checks if vehicle crash detection is supported on the device. The result depends on multiple criteria, such as if vehicle crash detection is enabled for your app, and if the necessary sensors are present on the device.

```objectivec
@property (nonatomic, readonly) BOOL isVehicleCrashDetectionSupported;
```

### wifiQuotaLimit

SDK WiFi quota limit

```objectivec
@property (nonatomic, readonly) long wifiQuotaLimit;
```

### wifiQuotaUsage

SDK WiFi quota usage

```objectivec
@property (nonatomic, readonly) long wifiQuotaUsage;
```

### mobileQuotaLimit

SDK mobile data quota limit

```
@property (nonatomic, readonly) long mobileQuotaLimit;
```

### mobileQuotaUsage

Get SDK mobile data quota usage

```
@property (nonatomic, readonly) long mobileQuotaUsage;
```

### diskQuotaLimit

SDK disk quota limit

```
@property (nonatomic, readonly) long diskQuotaLimit;
```

### diskQuotaUsage

SDK disk quota usage

```
@property (nonatomic, readonly) long diskQuotaUsage;
```

### `drivingInsightsProcessedDelegate`

Sets a delegate that will be invoked when the driving insights for a completed transport becomes ready.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
@property (nonatomic, strong) id <SENTDrivingInsightsReadyDelegate> _Nullable drivingInsightsProcessedDelegate;
```

<table><thead><tr><th width="318">Parameters</th><th></th></tr></thead><tbody><tr><td>drivingInsightsProcessedDelegate</td><td>A <a href="driving-insights/sentdrivinginsightsreadydelegate.md"><code>SENTDrivingInsightsReadyDelegate</code></a> to receive the driving insights. Set <code>nil</code> to remove a previously set delegate.</td></tr></tbody></table>



### initWithConfig: success: failure:

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [initializeWithOptions: launchOptions:](sentiance.md#initializewithoptions-launchoptions) instead.
{% endhint %}

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



### initializeWithOptions: launchOptions:

Initializes the Sentiance SDK.

```objectivec
- (SENTInitializationResult *)initializeWithOptions:(SENTOptions *)options
                                      launchOptions:(nullable NSDictionary *)launchOptions
NS_SWIFT_NAME(initialize(options:launchOptions:));
```



This method must be called on the main thread, inside&#x20;

```
[AppDelegate application:application didFinishLaunchingWithOptions:launchOptions]
```



It must not be called asynchronously, as doing so does not guarantee that it will be invoked before `application:didFinishLaunchingWithOptions:` completes.

For more details on this, see [SDK Initialization](https://docs.sentiance.com/sdk/appendix/sdk-initialization).

{% hint style="info" %}
Most SDK methods require an initialized SDK before being invoked, otherwise they throw a runtime exception. Methods excluded from this requirement mention this in their respective documentation.
{% endhint %}

{% hint style="warning" %}
You should initialize the SDK at most once, during app startup. Initializing it multiple times will normally fail with reason `SENTInitializationFailureReasonReinitializationNotAllowed`

unless a user does not exist yet (e.g. before user creation or after an SDK reset), in which case multiple initializations are still allowed.
{% endhint %}

<table><thead><tr><th width="236">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>options</td><td>the SDK initialization options.</td></tr><tr><td>launchOptions</td><td>the launch options obtained from <code>[AppDelegate application:application didFinishLaunchingWithOptions:launchOptions]</code></td></tr></tbody></table>

#### Returns: [SENTInitializationResult](https://app.gitbook.com/o/-LTy4edtsWdQgbEsKB-i/s/-LTy4edu-AQHCZBbSxqI/\~/changes/-Mdvb7zVAg9mTiQeb82W/sdk/api-reference/ios/sentinitializationresult)

###

### start:

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [enableDetectionsWithCompletionHandler: ](sentiance.md#enabledetectionswithcompletionhandler)instead.
{% endhint %}

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

###

### startWithStopDate: completion:

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [enableDetectionsWithExpiryDate: completionHandler:](sentiance.md#enabledetectionswithexpirydate-completionhandler) instead.
{% endhint %}



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

###

### stop

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [disableDetectionsWithCompletionHandler: ](sentiance.md#disabledetectionswithcompletionhandler)instead.
{% endhint %}

Stop the SDK.

```objectivec
- (void) stop;
```



### enableDetectionsWithCompletionHandler:

Enables SDK detections.

Requires a Sentiance user to be present on the device. Enabling detections is persistent across app restarts. Therefore, you do not need to call this method on every app startup. Once detections are enabled, as long as the SDK is properly initialized during startup, detections will be resumed, until you disable them by calling disableDetections. &#x20;

Enabling detections does not mean that the SDK is successfully able to start all detections. There may be unsatisfactory conditions that are blocking some detections. Check the DetectionStatus returned in the result to see if all detections are running and the SdkStatus to identify possible causes if not.

To automatically disable detections after some time, use the enableDetectionsWithExpiryDate: variant of this method.

Note: calling this method on an uninitialized SDK will throw an NSException.

```
- (void) enableDetectionsWithCompletionHandler: (nullable SENTEnableDetectionsCompletionHandler) completionHandler;
```

###

### enableDetectionsWithExpiryDate: completionHandler:

Enables SDK Detections with an expiry date at which detections get disabled.

Requires a Sentiance user to be present on the device. Enabling detections is persistent across app restarts. Therefore, you do not need to call this method on every app startup. Once detections are enabled, as long as the SDK is properly initialized during startup, detections will be resumed, until you disable them by calling disableDetections(), or they expire (see expirationDate).

Enabling detections does not mean that the SDK is successfully able to start all detections. There may be unsatisfactory conditions that are blocking some detections. Check the DetectionStatus returned in the result to see if all detections are running, and the sdkStatus to identify possible causes if not. &#x20;

This method has the same behaviour as enableDetections:, except an expiration date can be specified, as an absolute Date object, to automatically disable detections some time in the future. After having called this method with a future expiration date, you can cancel the expiration any time by calling enableDetections: again.

```objectivec
- (void) enableDetectionsWithExpiryDate: (nullable NSDate*) expiryDate
                      completionHandler: (nullable SENTEnableDetectionsCompletionHandler) completionHandler
NS_SWIFT_NAME(enableDetections(expiryDate:completionHandler:));
```

###

### disableDetectionsWithCompletionHandler:

Disables SDK detections.

Currently, this operation always succeeds. However, this behaviour may change in the future.

&#x20;Also throws NSException – if the SDK is not initialized.

```objectivec
- (void) disableDetectionsWithCompletionHandler: (nullable SENTDisableDetectionsCompletionHandler) completionHandler;
```

###

### createUserWithOptions: completionHandler:

Creates a Sentiance user if one does not yet exist.

Most SDK functionality requires a Sentiance user to be present on the device. Therefore, create a user first before enabling detections or interacting with other SDK features.

Parameter: [`Options`](https://app.gitbook.com/o/-LTy4edtsWdQgbEsKB-i/s/-LTy4edu-AQHCZBbSxqI/\~/changes/-Mdvb7zVAg9mTiQeb82W/sdk/api-reference/ios/sentusercreation) - For creating a User.

Throws: NSException if the SDK is not initialized.

```objectivec
- (void)createUserWithOptions: (SENTUserCreationOptions*) options
            completionHandler: (nullable SENTUserCreationCompletionHandler) completionHandler
NS_SWIFT_NAME(createUser(options:completionHandler:));
```

###

### linkUserWithLinker: completionHandler:&#x20;

Links the Sentiance user to your app's user on the Sentiance Platform.

During the linking process, the SDK will invoke the supplied SENTUserLinker, and will pass to it an installation ID. Your app must then forward this installation ID to the Sentiance backend (via your backend), and initiate user linking. Finally, when the linking completes, you must invoke the proper linker callback to complete the process.

Here are the complete steps:

1. Call this method and supply a linker.
2. Your linker will be invoked during the process, and an installation ID will be supplied.
3. In your linker, forward the installation ID to your backend to initiate a linking request towards the Sentiance backend. This request will include the installation ID and your app's user identifier.
4. Retrieve the response from the Sentiance backend and forward the result to the app.
5. Based on the result, invoke the linker callback's success or failure method. The callback is supplied to your linker along with the installation ID.
6. If it was successful, the SDK will confirm the result with the Sentiance backend to complete the link.

This method is useful if you want to link a Sentiance user that was created without specifying a linker in the user creation options (thereby having created an unlinked user).

{% hint style="info" %}
With this method, a Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past linking request).

You can only link to an app user that is new to Sentiance. This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
{% endhint %}

**parameter:** [linker](user-creation-and-linking/user-linking/metauserlinker.md): the linker that the SDK will pass the installation ID to and execute success and failure closures according to result.

**throws:** NSException if the SDK is not initialized.

```objectivec
- (void)linkUserWithLinker: (SENTUserLinker) linker
         completionHandler: (nullable SENTUserLinkingCompletionHandler) completionHandler;
```

###

### linkUserWithAuthCode: completionHandler:&#x20;

Links the Sentiance user to your app's user on the Sentiance Platform.

Uses the supplied authentication code to find the app user. Therefore, before calling this method, make sure that you have obtained a valid code from the backend Sentiance API (thereby having initiated the first linking step). This code request is authenticated using a Sentiance API key, which must never be transmitted to the app. Hence why the request must come from your backend.

Here are the complete steps:

1. Retrieve the code in your app and supply it to this method.
2. Initiate an authentication code request via your backend towards the Sentiance backend. This request will include your app's user identifier, which will be temporarily coupled to the code that you will receive.
3. The SDK will forward the code to the Sentiance backend to complete the link.

This method is useful if you want to link a Sentiance user that was previously created without specifying a linker in the user creation options (thereby having created an unlinked user).

{% hint style="info" %}
With this method, a Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past authentication code request). You can only link to an app user that is new to Sentiance.

This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
{% endhint %}

**parameters:** authCode - a code obtained from the backend Sentiance API.

**throws:**  NSException if the SDK is not initialized.

```objectivec
- (void)linkUserWithAuthCode: (NSString *)authCode
           completionHandler: (nullable SENTUserLinkingCompletionHandler) completionHandler
NS_SWIFT_NAME(linkUser(authCode:completionHandler:));
```

###

### **requestUserAccessTokenWithCompletionHandler:**

Returns the user's API access token as a Token object, via the completion Handler.

The token might be refreshed during this call, in which case, a valid network connection is required. You can use this token to query the Sentiance API for the user's data.

**throws:**  NSException if the SDK is not initialized.

```objectivec
- (void)requestUserAccessTokenWithCompletionHandler: (SENTUserAccessTokenCompletionHandler) completionHandler;
```



### requestUserContextWithCompletionHandler:

Fetches the userContext which holds the information about events, activeMoments, activeSegments, lastKnownLocation, home and work venues.

```objectivec
- (void)requestUserContextWithCompletionHandler: (SENTRequestUserContextCompletionHandler) completionHandler;
```

###

### getUserId

{% hint style="warning" %}
**Deprecated**

`getUserId` is deprecated. Use [userId](sentiance.md#userid) instead.
{% endhint %}

Returns the user ID

```objectivec
- (NSString *) getUserId;
```

###

### getUserAccessToken:

{% hint style="warning" %}
**Deprecated**

`getUserAccessToken` is deprecated. Use [requestUserAccessToken](sentiance.md#requestuseraccesstokenwithcompletionhandler) instead.
{% endhint %}

Returns the users Access Token if the user is authenticated

```objectivec
- (void) getUserAccessToken: (void (^)(NSString *token)) success 
                    failure: (void (^)(void)) failure;
```

###

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



### startTripWithMetadata: transportModeHint: completionHandler:

Starts an external trip. Requires a Sentiance user to be present on the device.

Calling this method interrupts any ongoing SDK detection, and forces the SDK to stay in a data collection mode. Trips started with this method may time out, in which case, the TripTimeoutListener set using setTripTimeoutListener(TripTimeoutListener) will be invoked.



The timeout duration can be configured for your app by Sentiance.

```objectivec
- (void)startTripWithMetadata: (nullable NSDictionary *) metadata
            transportModeHint: (SENTTransportMode)mode
            completionHandler: (nullable SENTStartTripCompletionHandler) completionHandler
NS_SWIFT_NAME(startTrip(metadata:transportModeHint:completionHandler:));

```



**parameters:**

metadata **-** A map of metadata pertaining to the newly started trip, which will be saved along with

the trip data, and made available in backend API query results and offloads. May be null.

mode - A hint of the transport mode being used, if known. May be \<code>null\</code>.

**throws:** NSException if the SDK is not initialized.



### startTrip: transportModeHint: success: failure:

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [startTripWithMetadata: transportModeHint: completionHandler:](sentiance.md#starttripwithmetadata-transportmodehint-completionhandler) instead.
{% endhint %}



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

###

### stopTrip: failure:

{% hint style="warning" %}
**Deprecated**

**T**his method is deprecated. Use [stopTripWithCompletionHandler:](sentiance.md#stoptripwithcompletionhandler) instead.
{% endhint %}

Stop a trip.

```objectivec
- (void) stopTrip: (void (^)(void)) success 
          failure: (void (^)(SENTSDKStatus* status)) failure;
```

###

### stopTripWithCompletionHandler:

Stops the currently ongoing external trip (i.e one that was started by calling startTrip()

Throws: NSException if the SDK is not initialized.

```
- (void)stopTripWithCompletionHandler: (nullable SENTStopTripCompletionHandler) completionHandler; 
```

###

### setTripTimeOutListener:

Set a trip timeout block.&#x20;

```objectivec
- (void) setTripTimeOutListener: (void (^)(void)) tripDidTimeOut;
```

{% hint style="info" %}
**tripDidTimeOut** block will be called each time trip will time out
{% endhint %}

###

### isVehicleCrashDetectionSupported:

Checks if vehicle crash detection is supported on the device for the specified trip type.

&#x20;The result depends on multiple criteria, such as if vehicle crash detection is enabled for your app, and if the necessary sensors are present on the device.

```objectivec
- (BOOL)isVehicleCrashDetectionSupported:(SENTTripType)tripType;
```

| Parameter |                                              |
| --------- | -------------------------------------------- |
| tripType  | The type of trip for which you want to check |

###

### invokeDummyVehicleCrash

Invokes a dummy vehicle crash event. Use this method to test your vehicle crash detection integration.

Calling this method will invoke the handler from [`setVehicleCrashHandler:`](sentiance.md#setvehiclecrashhandler)or [`setCrashListener:`](sentiance.md#setcrashlistener)depending on which handler was set last.

```objectivec
- (void)invokeDummyVehicleCrash;
```

{% hint style="info" %}
This method is intended for testing your integration, and not for production use.
{% endhint %}

###

### setCrashListener:

{% hint style="warning" %}
**Deprecated**

[`setCrashListener:`](sentiance.md#setcrashlistener) is deprecated. Use [`setVehicleCrashHandler:`](sentiance.md#setvehiclecrashhandler) instead.
{% endhint %}

Set vehicle crash detection block.&#x20;

```objectivec
- (void)setCrashListener:(void (^)(NSDate *date, CLLocation *lastKnownLocation))crashCallback;
```



### setVehicleCrashHandler:

Sets a handler that is invoked when a vehicle crash is detected with an instance of [`SENTVehicleCrashEvent`](sentvehiclecrashevent.md).

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

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [submitDetectionsWithCompletionHandler:](sentiance.md#submitdetectionswithcompletionhandler) instead.
{% endhint %}

Submits all the pending detections to backend, without considering any quota related updates and returns the status of these submissions via a callback to the enclosing app.

```objectivec
- (void) submitDetections: (void (^)(void)) success 
                  failure: (void (^)(void)) failure;
```

| Parameter |                                                                       |
| --------- | --------------------------------------------------------------------- |
| success   | Success block which is to be called when forced submission completes. |
| failure   | Failure block which is to be called when forced submission completes. |



### submitDetectionsWithCompletionHandler:

Submits any pending SDK detection to the Sentiance API.

This method will bypass any network quota limitation set for the SDK. A typical use case would be when the enclosing app determines (via diskQuotaUsage or diskQuotaStatus) that there are too many detections on disk that have not yet been submitted.

Throws: NSException if the SDK is not initialized.



### getInitState

{% hint style="warning" %}
**Deprecated**

This method is deprecated. Use [initState](sentiance.md#initstate) property instead.
{% endhint %}

Return state of inialization of the SDK: **SENTNotInitialized**, **SENTInitInProgress**, **SENTInitialized**

```objectivec
- (SENTSDKInitState) getInitState;
```

###

### getSdkStatus

{% hint style="warning" %}
**Deprecated**

Use [sdkStatus](sentiance.md#sdkstatus) property instead.
{% endhint %}

Get SDK status information

```objectivec
- (SENTSDKStatus*) getSdkStatus;
```

### getVersion

{% hint style="warning" %}
**Deprecated**

Use [version](sentiance.md#version) property instead.
{% endhint %}

Get SDK version

```objectivec
- (NSString *) getVersion;
```



### getWifiQuotaLimit

{% hint style="warning" %}
**Deprecated**

Use [`wifiQuotaLimit:`](sentiance.md#wifiquotalimit) property instead.
{% endhint %}

Get SDK WiFi quota limit

```objectivec
- (long) getWifiQuotaLimit;
```

### getWiFiQuotaUsage

{% hint style="warning" %}
**Deprecated**

Use [wifiQuotaUsage](sentiance.md#wifiquotausage) property instead.
{% endhint %}

Get SDK WiFi quota usage

```objectivec
- (long) getWiFiQuotaUsage;
```



### getMobileQuotaLimit

{% hint style="warning" %}
**Deprecated**

Use [`mobileQuotaLimit`](sentiance.md#mobilequotalimit) instead.
{% endhint %}

Get SDK mobile data quota limit

```objectivec
- (long) getMobileQuotaLimit;
```



### getMobileQuotaUsage

{% hint style="warning" %}
**Deprecated**

Use [mobileQuotaUsage](sentiance.md#mobilequotausage) instead.
{% endhint %}

Get SDK mobile data quota usage

```objectivec
- (long) getMobileQuotaUsage;
```

### getDiskQuotaLimit

{% hint style="warning" %}
**Deprecated**

Use [diskQuotaLimit](sentiance.md#diskquotalimit) property instead.
{% endhint %}

Get SDK disk quota limit

```objectivec
- (long) getDiskQuotaLimit;
```



### getDiskQuotaUsage&#x20;

{% hint style="warning" %}
**Deprecated**

Use [diskQuotaUsage:](sentiance.md#diskquotausage) instead.
{% endhint %}

Get SDK disk quota usage

```objectivec
- (long) getDiskQuotaUsage;
```



### resetWithCompletionHandler:

Resets the Sentiance SDK.

Calling this method results in stopping of all SDK operations and the deletion of all user data from the device. To avoid losing unsubmitted detection data, you can call submitDetections() before resetting the SDK as a final (best effort) attempt. However, keep in mind that this can introduce a delay to your reset process, since it is impacted by the network capability and the number of pending detections.

During an ongoing reset operation, calling any other SDK method will be ignored, fail, or will return a default result. After the reset operation completes, you do not have to reinitialize the SDK, but can do so by calling initialize(SentianceOptions)} again (e.g. to supply a different SentianceOptions).

While resetting, make sure that your app is in the foreground to prevent process termination (i.e. an activity is open, or a foreground service is running). The SDK cannot guarantee the completion of this operation otherwise.

You may call this method without having initialized the SDK.

<table><thead><tr><th width="219">Parameter</th><th></th></tr></thead><tbody><tr><td>completionHandler</td><td>a completion handler to receive the result of the reset operation.</td></tr></tbody></table>

```objectivec
- (void)resetWithCompletionHandler: (nullable SENTResetCompletionHandler)completionHandler;
```

### reset: failure:

{% hint style="warning" %}
**Deprecated**

Use [resetWithCompletionHandler**:**](sentiance.md#resetwithcompletionhandler) instead.
{% endhint %}

{% hint style="info" %}
The reset functionality is intended for removing all data in the device to handle a case such as a user logging out from an app or user requesting data deletion in the local app. It should not be used to reset the internal state of the SDK.
{% endhint %}

Resets the Sentiance SDK. Calling this method results in stopping of all SDK operations and deleting all SDK user data from the device. Additionally, the SDK will be uninitialized, allowing reinitialization and new Sentiance user creation.

The reset operation may take a while, in which case the SDK's initialization state will be set to [InitState](sentsdkstatus.md#sentsdkinitstate) **SENTResetting** until it is complete. Calling any other SDK method during this time will either be ignored or return a default value.&#x20;

Note that calling this method during intermediate initialization states (i.e. [InitState ](sentsdkstatus.md#sentsdkinitstate)**SENTInitInProgress**} and [InitState](sentsdkstatus.md#sentsdkinitstate) **SENTResetting** will fail.

```objectivec
- (void)reset:(void(^)(void))success failure:(void(^)(SENTResetFailureReason reason))failure;
```

| Parameter |                                                                                                              |
| --------- | ------------------------------------------------------------------------------------------------------------ |
| success   | Success block callback when reset successfully done                                                          |
| failure   | Failure callback when with one of [SENTResetFailureReason](sentsdkstatus.md#sentresetfailurereason) happened |

### setDidReceiveSdkStatusUpdateHandler:

Sets a handler that is invoked when the SDK's status is updated.

```objectivec
- (void) setDidReceiveSdkStatusUpdateHandler:(void (^) (SENTSDKStatus * status))handler;
```

| Parameter |                                                                                       |
| --------- | ------------------------------------------------------------------------------------- |
| handler   | a handler to receive SDK status updates, or nil to remove the previously set handler. |

### setVehicleCrashDiagnosticHandler:

Sets a handler that is invoked when a vehicle crash diagnostic is detected.

<table><thead><tr><th width="291">Parameter</th><th></th></tr></thead><tbody><tr><td>vehicleCrashDiagnosticHandler</td><td>a handler to receive vehicle crash diagnostics of type <a href="sentvehiclecrashdiagnostic.md">SENTVehicleCrashDiagnostic</a></td></tr></tbody></table>

**throws:**  NSException if the SDK is not initialized.

```objectivec
- (void)setVehicleCrashDiagnosticHandler:(void (^)(SENTVehicleCrashDiagnostic *vehicleCrashDiagnostic))vehicleCrashDiagnosticHandler;
```

### setTransmittableDataTypes:

Set the data types that are allowed to be sent to the Sentiance Cloud Platform.

This configuration is persistent across app restarts, but will be cleared upon SDK reset.

**Note:** this configuration is not applicable to logging and diagnostic data that may get uploaded to the Sentiance Cloud Platform (if enabled for your app).

<table><thead><tr><th width="291">Parameter</th><th></th></tr></thead><tbody><tr><td>transmittableDataTypes</td><td>data types of type <a href="senttransmittabledatatype.md">SENTTransmittableDataType</a>.</td></tr></tbody></table>

**throws:**  NSException if the SDK is not initialized.

```objectivec
- (void)setTransmittableDataTypes:(NSSet<NSNumber *> *)transmittableDataTypes NS_REFINED_FOR_SWIFT;
```

### transmittableDataTypes

Returns a set of [SENTTransmittableDataType](senttransmittabledatatype.md) data types that are allowed to be sent to the Sentiance Cloud Platform.

**throws:**  NSException if the SDK is not initialized.

```objectivec
- (NSSet<NSNumber *> *)transmittableDataTypes NS_REFINED_FOR_SWIFT;
```

### enableTransportSessionRecording

Enables transport session recording.

This setting is persistent across app restarts, so you only need to enable session recording once. Note however that the setting is reset to `disabled` after an SDK reset. See [reset](sentiance.md#resetwithcompletionhandler).

Recorded sessions are stored on the device until the time that you request their deletion. See [`deleteTransportSession(String)`](sentiance.md#deletetransportsession).

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (void)enableTransportSessionRecording;
```

### `disableTransportSessionRecording`

Disables transport session recording.

This setting is persistent across app restarts, so you only need to disable session recording once.

If you no longer need session recording, make sure to delete previously recorded sessions if you no longer need them. See [`deleteAllTransportSessions()`](sentiance.md#deletealltransportsessions).

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (void)disableTransportSessionRecording;
```

### `getAvailableTransportSessions`

Returns a list of recorded and completed transport sessions.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (NSArray<SENTTransportSession *> *)getAvailableTransportSessions;
```

### `isTransportSessionRecordingEnabled`

Returns whether transport session recording is enabled.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (BOOL)isTransportSessionRecordingEnabled;
```

### `setTransportSessionHandler`

Sets a handler that will be invoked to deliver transport sessions. A session is delivered after a transport ends.

Transport sessions are stored on the device until the time that you request their deletion. See [`deleteTransportSession(String)`](sentiance.md#deletetransportsession).

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (void)setTransportSessionHandler:(void (^)(SENTTransportSession *transportSession))transportSessionHandler;
```

<table><thead><tr><th width="182">Parameters</th><th></th></tr></thead><tbody><tr><td>transportSessionHandler</td><td>A transportSessionHandler to receive <a href="transport-sessions/senttransportsession.md">transport sessions,</a> or <code>nil</code> to remove a previously set handler.</td></tr></tbody></table>

### `deleteAllTransportSessions`

Deletes all recorded transport sessions.

Recorded sessions are stored on the device. It is your responsibility to call this method, or [`deleteTransportSession(String)`](sentiance.md#deletetransportsession), to request their deletion, when you no longer need them.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (void)deleteAllTransportSessions;
```

### `deleteTransportSession`

Deletes the transport session with the specified ID.

Recorded sessions are stored on the device. It is your responsibility to call this method, or [`deleteAllTransportSessions`](sentiance.md#deletealltransportsessions), to request their deletion, when you no longer need them.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (void)deleteTransportSession:(NSString *)sessionId NS_SWIFT_NAME(deleteTransportSession(sessionId:));
```

<table><thead><tr><th width="253">Parameters</th><th></th></tr></thead><tbody><tr><td>sessionId</td><td>The ID of the session to delete.</td></tr></tbody></table>

### `getDrivingInsights`

Returns the [driving insights](driving-insights/sentdrivinginsights.md) for a given transport, or `nil` if there are no driving insights or the transport ID is invalid.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (SENTDrivingInsights * _Nullable)getDrivingInsightsForTransportId:(NSString * _Nonnull)transportId;
```

<table><thead><tr><th width="243">Parameters</th><th></th></tr></thead><tbody><tr><td>transportId</td><td>The ID of the desired transport.</td></tr></tbody></table>

### `getHarshDrivingEvents`

Returns the [harsh driving events](driving-insights/sentharshdrivingevent.md) for a completed transport.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (NSArray<SENTHarshDrivingEvent *> * _Nonnull)getHarshDrivingEventsForTransportId:(NSString * _Nonnull)transportId; 
```

<table><thead><tr><th width="244">Parameters</th><th></th></tr></thead><tbody><tr><td>transportId</td><td>The ID of the desired transport.</td></tr></tbody></table>

### `getPhoneUsageEvents`

Returns the [phone usage events](driving-insights/sentphoneusageevent.md) for a completed transport.

Note: calling this method on an uninitialized SDK will throw an NSException.

```objectivec
- (NSArray<SENTPhoneUsageEvent *> * _Nonnull)getPhoneUsageEventsForTransportId:(NSString * _Nonnull)transportId; 
```

<table><thead><tr><th width="244">Parameters</th><th></th></tr></thead><tbody><tr><td>transportId</td><td>The ID of the desired transport.</td></tr></tbody></table>
