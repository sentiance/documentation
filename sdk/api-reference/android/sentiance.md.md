# Sentiance

The Sentiance class is the main entry point for interacting with the SDK. This class is a singleton, therefore you can obtain an instance as follows:

```java
Sentiance sentianceSDK = Sentiance.getInstance(context);
```

{% hint style="warning" %}
With the exception of the following methods, all other methods in this class will throw an [`SDKException`](sdkexception.md) exception when invoked before SDK initialization is complete. See[`initialize(SentianceOptions)`](sentiance.md.md#initialize-sentianceoptions).

* `initialize(SentianceOptions)`
* `initialize()`
* `init(SdkConfig, OnInitCallback)` - Deprecated
* `userExists()`
* `isUserLinked()`
* `reset()`
* `reset(ResetCallback)` - Deprecated
* `getInitState()`
* `getVersion()`
{% endhint %}

## Sentiance API

### `addUserMetadataField()`

> ```java
> void addUserMetadataField(String label, String value)
> ```
>
> Adds a user specific metadata field.

| Parameters |                        |
| ---------- | ---------------------- |
| label      | Metadata label to add. |
| value      | Metadata value.        |

### `addUserMetadataFields()`

> ```java
> void addUserMetadataFields(Map<String, String> metadata)
> ```
>
> Adds multiple user specific metadata fields.

| Parameters |                      |
| ---------- | -------------------- |
| metadata   | The metadata fields. |

### `addTripMetadata()`

> ```java
> boolean addTripMetadata(Map<String, String> metadata)
> ```
>
> Adds metadata while an external trip is ongoing. This method can be called multiple times during a trip.
>
> This method returns false if there is no ongoing external trip or `null` metadata is passed.

| Parameters |                                                                                                 |
| ---------- | ----------------------------------------------------------------------------------------------- |
| metadata   | A map of metadata pertaining to the ongoing trip, which will be saved along with the trip data. |

### `createUser()`

> ```java
> PendingOperation<UserCreationResult, UserCreationError> createUser(UserCreationOptions options)
> ```
>
> Creates a Sentiance user if one does not yet exist.
>
> Most SDK functionality requires a Sentiance user to be present on the device. Therefore, create a user first before enabling detections or interacting with other SDK features.
>
> Returns [`UserCreationResult`](usercreationresult/) upon success or [`UserCreationError`](usercreationerror/) upon failure via [PendingOperation](pendingoperation/).

| Parameters |                                                                           |
| ---------- | ------------------------------------------------------------------------- |
| options    | A [UserCreationOptions](usercreationoptions/) object for creating a user. |

### `disableBatteryOptimization()`

> ```java
> void disableBatteryOptimization()
> ```
>
> Generates a system dialog asking the user to allow disabling battery optimization for the app.
>
> Learn more about disabling battery optimization [here](../../appendix/android/android-battery-optimization.md).

### `disableDetections()`

> ```java
> PendingOperation<DisableDetectionsResult, DisableDetectionsError> disableDetections()
> ```
>
> Disables SDK detections. Currently, this operation always succeeds. However, this behaviour may change in the future.
>
> Returns [`DisableDetectionsResult`](disabledetectionsresult.md) upon success or [`DisableDetectionsError`](disabledetectionserror.md) upon failure via [PendingOperation](pendingoperation/).

### `enableDetections()`

> ```java
> PendingOperation<EnableDetectionsResult, EnableDetectionsError> enableDetections()
> ```
>
> Enables SDK detections. Requires a Sentiance user to be present on the device. Enabling detections is persistent across app restarts. Therefore, you do not need to call this method on every app startup. Once detections are enabled, as long as the SDK is properly initialized during startup, detections will be resumed, until you disable them by calling [`disableDetections()`](sentiance.md.md#disabledetections).
>
>
>
> Enabling detections does not mean that the SDK is successfully able to start all detections. There may be unsatisfactory conditions that are blocking some detections. Check the DetectionStatus returned in the result to see if all detections are running, and the SdkStatus to identify possible causes if not.
>
>
>
> To automatically disable detections after some time, use the [`enableDetections(Date)`](sentiance.md.md#enabledetections) variant of this method.
>
>
>
> Returns [`EnableDetectionsResult`](enabledetectionsresult.md) upon success or [`EnableDetectionsError`](enabledetectionserror/) upon failure via [PendingOperation](pendingoperation/).

### `enableDetections(Date)`

> ```java
> PendingOperation<EnableDetectionsResult, EnableDetectionsError> enableDetections(@Nonnull Date expirationDate)
> ```
>
> Enables SDK detections. Requires a Sentiance user to be present on the device. Enabling detections is persistent across app restarts. Therefore, you do not need to call this method on every app startup. Once detections are enabled, as long as the SDK is properly initialized during startup, detections will be resumed, until you disable them by calling [`disableDetections()`](sentiance.md.md#disabledetections).
>
>
>
> Enabling detections does not mean that the SDK is successfully able to start all detections. There may be unsatisfactory conditions that are blocking some detections. Check the DetectionStatus returned in the result to see if all detections are running, and the SdkStatus to identify possible causes if not.
>
>
>
> This method has the same behaviour as [`enableDetections()`](sentiance.md.md#enabledetections), except an expiration date can be specified, as an absolute `Date` object, to automatically disable detections some time in the future. After having called this method with a future expiration date, you can cancel the expiration any time by calling [`enableDetections()`](sentiance.md.md#enabledetections) again.
>
>
>
> Returns [`EnableDetectionsResult`](enabledetectionsresult.md) upon success or [`EnableDetectionsError`](enabledetectionserror/) upon failure via [PendingOperation](pendingoperation/).

| Parameters     |                                                                               |
| -------------- | ----------------------------------------------------------------------------- |
| expirationDate | An absolute date at which detections should automatically get disabled again. |

### `getDetectionStatus()`

> ```java
> DetectionStatus getDetectionStatus()
> ```
>
> Returns the [DetectionStatus](detectionstatus.md).

### `getDiskQuotaLimit()`

> ```java
> long getDiskQuotaLimit()
> ```
>
> Returns the SDK's disk quota limit in bytes.

### `getDiskQuotaUsage()`

> ```java
> long getDiskQuotaUsage()
> ```
>
> Returns the SDK's disk quota usage in bytes.

### `getInitState()`

> ```java
> InitState getInitState()
> ```
>
> Returns the initialization state of the Sentiance SDK.

### `getInstance()`

> ```java
> static Sentiance getInstance(Context context)
> ```
>
> Returns an instance of the [`Sentiance`](sentiance.md.md) class.
>
> This method will call [`Context.getApplicationContext()`](https://developer.android.com/reference/android/content/Context.html#getApplicationContext\(\)) on the passed context to prevent memory leaks when passing an Activity context.

| Parameters |                                                                                        |
| ---------- | -------------------------------------------------------------------------------------- |
| context    | A [`Context`](https://developer.android.com/reference/android/content/Context) object. |

### `getMobileQuotaLimit()`

> ```java
> long getMobileQuotaLimit()
> ```
>
> Returns the SDK's mobile data quota limit in bytes.

### `getMobileQuotaUsage()`

> ```java
> long getMobileQuotaUsage()
> ```
>
> Returns the SDK's mobile data quota usage in bytes.

### `getSdkStatus()`

> ```java
> SdkStatus getSdkStatus()
> ```
>
> Returns an [`SdkStatus`](sdkstatus/) object representing the state of the SDK.

### `getUserActivity()`

> ```java
> UserActivity getUserActivity()
> ```
>
> Returns a [`UserActivity`](useractivity.md) object representing the currently detected user's activity.

### `getUserAccessToken()`

{% hint style="warning" %}
This method is deprecated. Use [`requestUserAccessToken`](sentiance.md.md#requestuseraccesstoken) instead.
{% endhint %}

> ```java
> void getUserAccessToken(TokenResultCallback callback)
> ```
>
> Returns the user's API access token as a [`Token`](token.md) object via the specified callback.
>
> For more information regarding failure, see [`TokenResultCallback.onFailure()`](tokenresultcallback.md#onfailure).

| Parameters |                                                                                                                                                                                                                                                                                               |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| callback   | A callback to handle the token result. Note that the SDK holds a [weak reference](https://developer.android.com/reference/java/lang/ref/WeakReference) to this callback in order to prevent component leaks. Make sure you have a strong reference to it in order to guarantee its execution. |

### `getUserId()`

> ```java
> @Nullable String getUserId()
> ```
>
> Returns the Sentiance user ID, or `null` if authentication has not yet succeeded.

### `getVersion()`

> ```java
> String getVersion()
> ```
>
> Returns the SDK version as a String.

### `getWiFiQuotaLimit()`

> ```java
> long getWiFiQuotaLimit()
> ```
>
> Returns the SDK's WiFi quota limit in bytes.

### `getWiFiQuotaUsage()`

> ```java
> long getWiFiQuotaUsage()
> ```
>
> Returns the SDK's WiFi quota usage in bytes.

### `initialize()`

> ```java
> InitializationResult initialize()
> ```
>
> Initializes the Sentiance SDK, thereby preparing it to resume detections if a Sentiance user exists, and if detections were last enabled. If a user does not exist, this method does only minimal work to allow user creation. To create a user, call [`createUser(UserCreationOptions)`](sentiance.md.md#createuser).
>
>
>
> To ensure proper continuity of SDK detections across app restarts, this method must be called inside {@link Application#onCreate()}, on the main application thread, before onCreate returns. The call must not be offloaded to a background thread, as doing so cannot guarantee its invocation prior to the completion of the app startup. For more information about this requirement, see: [SDK Initialization](https://docs.sentiance.com/sdk/appendix/sdk-initialization).
>
> You should initialize the SDK at most once, normally during app startup. Initializing it multiple times will fail with reason [`InitializationFailureReason#REINITIALIZATION_NOT_ALLOWED`](initializationresult/initializationfailurereason.md), unless a Sentiance user does not yet exist (e.g. before user creation, or after an SDK reset), in which case multiple invocations of this method are still allowed.
>
>
>
> Note that most SDK methods require an initialized SDK before being invoked, otherwise they throw a runtime exception. Methods excluded from this requirement indicate this in their respective documentation.
>
> Returns the [`InitializationResult`](initializationresult/).

### `initialize(SentianceOptions)`

> ```java
> InitializationResult initialize(SentianceOptions options)
> ```
>
> Initializes the Sentiance SDK, thereby preparing it to resume detections if a Sentiance user exists, and if detections were last enabled. If a user does not exist, this method does only minimal work to allow user creation. To create a user, call [`createUser(UserCreationOptions)`](sentiance.md.md#createuser).
>
>
>
> To ensure proper continuity of SDK detections across app restarts, this method must be called inside {@link Application#onCreate()}, on the main application thread, before onCreate returns. The call must not be offloaded to a background thread, as doing so cannot guarantee its invocation prior to the completion of the app startup. For more information about this requirement, see: [SDK Initialization](https://docs.sentiance.com/sdk/appendix/sdk-initialization).
>
> You should initialize the SDK at most once, normally during app startup. Initializing it multiple times will fail with reason [`InitializationFailureReason#REINITIALIZATION_NOT_ALLOWED`](initializationresult/initializationfailurereason.md), unless a Sentiance user does not yet exist (e.g. before user creation, or after an SDK reset), in which case multiple invocations of this method are still allowed.
>
>
>
> Note that most SDK methods require an initialized SDK before being invoked, otherwise they throw a runtime exception. Methods excluded from this requirement indicate this in their respective documentation.
>
> Returns the [`InitializationResult`](broken-reference).

| Parameters                            |                             |
| ------------------------------------- | --------------------------- |
| [SentianceOptions](sentianceoptions/) | SDK initialization options. |

### `init()`

{% hint style="warning" %}
This method is deprecated. Use [`initialize()`](sentiance.md.md#initialize) or [`initialize(SentianceOptions)`](sentiance.md.md#initialize-sentianceoptions) instead.
{% endhint %}

> ```java
> void init(SdkConfig sdkConfig, final OnInitCallback initCallback)
> ```
>
> Initializes the Sentiance Sdk.&#x20;
>
> This method constructs internal SDK components and prepares the SDK for handling app and system requests. If a Sentiance user does not yet exist on the device, this method triggers user creation on the Sentiance Platform, which requires internet connectivity.
>
> During the lifetime of the app process, calling this method again after a successful initialization is not allowed. Doing so is regarded as an error and therefore throws an [`SdkException`](sdkexception.md) at runtime. To reinitialize the SDK with a different configuration or to create a new Sentiance user, first call [`reset(ResetCallback)`](sentiance.md.md#reset-resetcallback).
>
> All methods in this class (except this method, [`reset(ResetCallback)`](sentiance.md.md#reset-resetcallback), [`getInitState()`](sentiance.md.md#getinitstate) and [`getVersion()`](sentiance.md.md#getversion)) will throw an [`SdkException`](sdkexception.md) when called before initialization has completed.

| Parameters   |                                                                                 |
| ------------ | ------------------------------------------------------------------------------- |
| sdkConfig    | An [`SdkConfig`](sdkconfig/) representing the SDK configuration.                |
| initCallback | An [`OnInitCallback`](oninitcallback/) to handle the initialization of the Sdk. |

### `isAppSessionDataCollectionEnabled()`

> ```java
> boolean isAppSessionDataCollectionEnabled()
> ```
>
> Returns whether app session data collection is enabled. See [`setAppSessionDataCollectionEnabled(boolean)`](sentiance.md.md#setappsessiondatacollectionenabled).

### `isTripOngoing()`

> ```java
> boolean isTripOngoing(TripType tripType)
> ```
>
> Indicates whether a trip is in progress.

| Parameters |                                                                                                |
| ---------- | ---------------------------------------------------------------------------------------------- |
| tripType   | A [`TripType`](trip/triptype.md) enum indicating the type of trip the caller is interested in. |

### `userExists()`

> ```java
> boolean userExists()
> ```
>
> Checks if a Sentiance user exists on the device.
>
> You may call this method without having initialized the SDK.

### `isUserLinked()`

> ```java
> boolean isUserLinked()
> ```
>
> Checks if a Sentiance user exists on the device, and whether it is linked to your app's user.
>
> You may call this method without having initialized the SDK.

### `linkUser(String)`

> ```java
> PendingOperation<UserLinkingResult, UserLinkingError> linkUser(String authenticationCode)
> ```
>
> Links the Sentiance user to your app's user, on the Sentiance Platform. Uses the supplied authentication code to find the app user. Therefore, before calling this method, make sure that you have obtained a valid code from the backend Sentiance API (thereby having initiated the first linking step). This code request is authenticated using a Sentiance API key, which must never be transmitted to the app. Hence why the request must come from your backend.
>
> \
> Here are the complete steps:
>
> 1. Initiate an authentication code request via your backend towards the Sentiance backend. This request will include your app's user identifier, which will be temporarily coupled to the code that you will receive.
> 2. Retrieve the code in your app and supply it to this method.
> 3. The SDK will forward the code to the Sentiance backend to complete the link.
>
> This method is useful if you want to link a Sentiance user that was created by specifying the [`UserLinker#NO_OP`](userlinker.md#no\_op) or [`UserLinkerAsync#NO_OP`](userlinkerasync.md#no\_op) linker in the user creation options (thereby having created an unlinked user).
>
>
>
> Note that with this method, a Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past authentication code request). You can only link to an app user that is new to Sentiance. This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
>
> \
> Returns [`UserLinkingResult`](userlinkingresult.md) upon success or [`UserLinkingError`](userlinkingerror/) upon failure via [PendingOperation](pendingoperation/).

| Parameters         |                                                 |
| ------------------ | ----------------------------------------------- |
| authenticationCode | A code obtained from the backend Sentiance API. |

### `linkUser(UserLinkerAsync)`

> ```java
> PendingOperation<UserLinkingResult, UserLinkingError> linkUser(UserLinkerAsync userLinker)
> ```
>
> Links the Sentiance user to your app's user, on the Sentiance Platform. During the linking process, the SDK will call the link method of the supplied [UserLinkerAsync](userlinkerasync.md), and will pass to it an installation ID. Your app must then forward this installation ID to the Sentiance backend (via your backend), and initiate user linking. Finally, when the linking completes, you must invoke the proper linker callback to complete the process.
>
>
>
> Here are the complete steps:
>
> 1. Call this method and supply a linker.
> 2. Your linker will be invoked during the process, and an installation ID will be supplied.
> 3. In your linker, forward the installation ID to your backend to initiate a linking request towards the Sentiance backend. This request will include the installation ID and your app's user identifier.
> 4. Retrieve the response from the Sentiance backend and forward the result to the app.
> 5. Based on the result, invoke the linker callback's success or failure method. The callback is supplied to your linker along with the installation ID.
> 6. If it was successful, the SDK will confirm the result with the Sentiance backend to complete the link.
>
>
>
> This method is useful if you want to link a Sentiance user that was created by specifying the [`UserLinker#NO_OP`](userlinker.md#no\_op) or [`UserLinkerAsync#NO_OP`](userlinkerasync.md#no\_op) linker in the user creation options (thereby having created an unlinked user).
>
> Note that with this method, a Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past authentication code request). You can only link to an app user that is new to Sentiance. This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
>
> \
> Returns [`UserLinkingResult`](userlinkingresult.md) upon success or [`UserLinkingError`](userlinkingerror/) upon failure via [PendingOperation](pendingoperation/).



| Parameters |                                                           |
| ---------- | --------------------------------------------------------- |
| userLinker | The linker that the SDK will pass the installation ID to. |

### `linkUser(UserLinker)`

> ```java
> PendingOperation<UserLinkingResult, UserLinkingError> linkUser(UserLinkerAsync userLinker)
> ```
>
> Links the Sentiance user to your app's user, on the Sentiance Platform. During the linking process, the SDK will call the link method of the supplied [`UserLinker`](userlinker.md), and will pass to it an installation ID. Your app must then forward this installation ID to the Sentiance backend (via your backend), and initiate user linking. Finally, when the linking completes, you must return a proper result to complete the process.
>
> \
> Here are the complete steps:
>
> 1. Call this method and supply a linker.
> 2. Your linker will be invoked during the process, and an installation ID will be supplied.
> 3. In your linker, forward the installation ID to your backend to initiate a linking request towards the Sentiance backend. This request will include the installation ID and your app's user identifier.
> 4. Retrieve the response from the Sentiance backend and forward the result to the app.
> 5. In your linker, return `true` if the result was successful, and otherwise return `false`.
> 6. If it was successful, the SDK will confirm the result with the Sentiance backend to complete the link.
>
> This method is useful if you want to link a Sentiance user that was created by specifying the [`UserLinker#NO_OP`](userlinker.md#no\_op) or [`UserLinkerAsync#NO_OP`](userlinkerasync.md#no\_op) linker in the user creation options (thereby having created an unlinked user).\
>
>
> Note that with this method, a Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past authentication code request). You can only link to an app user that is new to Sentiance. This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
>
> \
> Returns [`UserLinkingResult`](userlinkingresult.md) upon success or [`UserLinkingError`](userlinkingerror/) upon failure via [PendingOperation](pendingoperation/).

| Parameters |                                                           |
| ---------- | --------------------------------------------------------- |
| userLinker | The linker that the SDK will pass the installation ID to. |

### `removeUserMetadataField()`

> ```java
> void removeUserMetadataField(String label)
> ```
>
> Removes a user specific metadata field.

| Parameters |                     |
| ---------- | ------------------- |
| label      | Metadata to remove. |

### `requestUserAccessToken()`

> ```java
> PendingOperation<Token, UserAccessTokenError> requestUserAccessToken()
> ```
>
> Returns [`Token`](token.md) upon success or [`UserAccessTokenError`](useraccesstokenerror/) upon failure via [PendingOperation](pendingoperation/).

### `reset()`

{% hint style="danger" %}
The reset functionality is intended for removing all data in the device to handle a case such as a user logging out from an app or user requesting data deletion in the local app. It should not be used to reset the internal state of the SDK.
{% endhint %}

> ```java
> PendingOperation<ResetResult, ResetError> reset()
> ```
>
> Resets the Sentiance SDK.
>
> Calling this method results in stopping of all SDK operations and the deletion of all user data from the device. To avoid losing unsubmitted detection data, you can call [`submitDetections`](sentiance.md.md#submitdetections) before resetting the SDK as a final (best effort) attempt. However, keep in mind that this can introduce a delay to your reset process, since it is impacted by the network capability and the number of pending detections.
>
> During an ongoing reset operation, calling any other SDK method will be ignored, fail, or will return a default result. After the reset operation completes, you do not have to reinitialize the SDK, but can do so by calling [initialize(SentianceOptions)](sentiance.md.md#initialize-sentianceoptions) again (e.g. to supply a different [`SentianceOptions`](sentianceoptions/)).
>
> While resetting, make sure that your app is in the foreground to prevent process termination (i.e. an activity is open, or a foreground service is running). The SDK cannot guarantee the completion of this operation otherwise.
>
> You may call this method without having initialized the SDK
>
>
>
> Returns [`ResetResult`](resetresult.md) upon success or [`ResetError`](reseterror/) upon failure via [PendingOperation](pendingoperation/).

### `reset(ResetCallback)`

{% hint style="warning" %}
This method is deprecated. Use `reset()` instead.
{% endhint %}

{% hint style="danger" %}
The reset functionality is intended for removing all data in the device to handle a case such as a user logging out from an app or user requesting data deletion in the local app. It should not be used to reset the internal state of the SDK.
{% endhint %}

> ```java
> void reset(@Nullable ResetCallback callback)
> ```
>
> Resets the Sentiance SDK.
>
> Calling this method results in stopping of all SDK operations and deleting all SDK user data from the device. Additionally, the SDK will be uninitialized, allowing reinitialization and new Sentiance user creation.
>
> The reset operation may take a while, in which case the SDK's initialization state will be set to [`InitState.RESETTING`](initstate.md) until it's complete. Calling any other SDK method during this time will either be ignored or return a default value. While resetting, make sure your app is in the foreground to prevent process termination (i.e. an activity is open, or a foreground service is running).
>
> Note that calling this method during intermediate initialization states (i.e. [`INIT_IN_PROGRESS`](initstate.md) and [`RESETTING`](initstate.md)) will fail.

| Parameters |                                                                     |
| ---------- | ------------------------------------------------------------------- |
| callback   | A [`ResetCallback`](resetcallback/) to handle the reset completion. |

### `setAppSessionDataCollectionEnabled()`

> ```java
> void setAppSessionDataCollectionEnabled(boolean enabled)
> ```
>
> If enabled, the SDK may collect additional sensor and location data when the app is in the foreground (i.e visible to the user). This data may get uploaded to the Sentiance Platform. By default, this data collection is disabled.

### `setSdkStatusUpdateListener()`

> ```java
> void setSdkStatusUpdateListener(SdkStatusUpdateListener listener)
> ```
>
> Sets a listener that is invoked when the SDK's status is updated.

| Parameters |                                                                                                                                                |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| listener   | A [`SdkStatusUpdateListener`](sdkstatusupdatelistener.md) to receive a new [`SdkStatus`](sdkstatus/), or null to remove the previous listener. |

### `setTripTimeoutListener()`

> ```java
> void setTripTimeoutListener(@Nullable TripTimeoutListener listener)
> ```
>
> Sets a listener that is invoked when a trip times out.
>
> Currently, only external trips started by calling [`startTrip(Map,TransportMode)`](sentiance.md.md#starttrip-map-transportmode) time out, and only when your app is configured by Sentiance to run in "triggered trips" mode (where automatic SDK detections are disabled). Therefore, timeouts do not apply to most use-cases.

| Parameters |                                                                                                                          |
| ---------- | ------------------------------------------------------------------------------------------------------------------------ |
| listener   | A [`TripTimeoutListener`](trip/triptimeoutlistener.md) to handle trip timeouts, or null to remove the previous listener. |

### `setUserActivityListener()`

> ```java
> void setUserActivityListener(@Nullable UserActivityListener listener)
> ```
>
> Sets a listener that is invoked when a new user activity is detected. After calling this method, the current user activity will be immediately delivered to the listener.

| Parameters |                                                                                                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| listener   | A [`UserActivityListener`](useractivitylistener.md) to handle [`UserActivity`](useractivity.md) changes, or null to remove the previous listener. |

### `start()`

{% hint style="warning" %}
This method is deprecated. Use [`enableDetections()`](sentiance.md.md#enabledetections) instead.
{% endhint %}

> ```java
> void start(OnStartFinishedHandler handler)
> ```
>
> Starts the SDK detections.
>
> When this process has finished, [`OnStartFinishedHandler.onStartFinished(SdkStatus)`](onstartfinishedhandler.md#onstartfinished) will be called. This does not necessarily mean that the SDK is actually performing detections. You may use the [`SdkStatus`](sdkstatus/) passed to the [`onStartFinished(SdkStatus)`](onstartfinishedhandler.md#onstartfinished) method to determine why.
>
> To automatically stop detections, call the [`start(Date, OnStartFinishedHandler)`](sentiance.md.md#start-date-onstartfinishedhandler) method instead. You do not need to call [`stop()`](sentiance.md.md#stop) beforehand as all start calls override each other.

| Parameters |                                                                                                                                                                                                                                                                                                                                                                  |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| handler    | A [`OnStartFinishedHandler`](onstartfinishedhandler.md) used to notify that the SDK start has finished. Note that the SDK holds a [weak reference](https://developer.android.com/reference/java/lang/ref/WeakReference) to this handler to in order to prevent component leaks. Make sure you have a strong reference to it in order to guarantee its execution. |

### `start(Date, OnStartFinishedHandler)`

{% hint style="warning" %}
This method is deprecated. Use [`enableDetections(Date)`](sentiance.md.md#enabledetections-date) instead.
{% endhint %}

> ```java
> void start(Date stopDate, OnStartFinishedHandler handler)
> ```
>
> Starts the SDK detections.
>
> This method has the same behaviour as [`start(OnStartFinishedHandler)`](sentiance.md.md#start) except an absolute date is passed to automatically stop the SDK some time in the future. A typical use-case is when the app provides a free trial period for its users after which the SDK should stop running.
>
> To cancel the auto-stop functionality, you can call this method with a null stopDate or just call [`start(OnStartFinishedHandler)`](sentiance.md.md#start). You do not need to call [`stop()`](sentiance.md.md#stop) beforehand as all start calls override each other.

| Parameters |                                                                                                                                                                                                                                                                                                                                                                  |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| stopDate   | An absolute date at which the SDK is stopped. If the date is in the past, the SDK will stop immediately.                                                                                                                                                                                                                                                         |
| handler    | A [`OnStartFinishedHandler`](onstartfinishedhandler.md) used to notify that the SDK start has finished. Note that the SDK holds a [weak reference](https://developer.android.com/reference/java/lang/ref/WeakReference) to this handler to in order to prevent component leaks. Make sure you have a strong reference to it in order to guarantee its execution. |

### `startTrip(Map, TransportMode)`

> ```java
> PendingOperation<StartTripResult, StartTripError> startTrip(@Nullable Map<String, String> metadata,
>  				                            @Nullable TransportMode transportModeHint)
> ```
>
> Starts an external trip. Requires a Sentiance user to be present on the device.
>
> Calling this method interrupts any ongoing SDK detection, and forces the SDK to stay in a data collection mode. Trips started with this method may time out, in which case, the [TripTimeoutListener](trip/triptimeoutlistener.md) set using [`setTripTimeoutListener(TripTimeoutListener)`](sentiance.md.md#settriptimeoutlistener) will be invoked. The timeout duration can be configured for your app by Sentiance.
>
> To learn more about external trips, see [controlled detections](../../appendix/controlled-detections/).
>
> \
> Returns [`StartTripResult`](starttripresult.md) upon success or [`StartTripError`](starttriperror/) upon failure via [PendingOperation](pendingoperation/).

| Parameters        |                                                                                                                                                                                    |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| metadata          | A map of metadata pertaining to the newly started trip, which will be saved along with the trip data, and made available in backend API query results and offloads. May be `null`. |
| transportModeHint | A [`TransportMode`](trip/transportmode.md) hint indicating the type of transport being used, if known.                                                                             |

### `startTrip(Map, TransportMode, StartTripCallback)`

{% hint style="warning" %}
This method is deprecated. Use [startTrip(Map, TransportMode)](sentiance.md.md#starttrip-map-transportmode) instead.
{% endhint %}

> ```java
> void startTrip(@Nullable Map<String, String> metadata, 
>                @Nullable TransportMode transportModeHint, 
>                @Nullable StartTripCallback callback)
> ```
>
> Starts an external trip.
>
> To learn more about external trips, see [controlled detections](../../appendix/controlled-detections/).

| Parameters        |                                                                                                        |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| metadata          | A map of metadata pertaining to the newly started trip, which will be saved along with the trip data.  |
| transportModeHint | A [`TransportMode`](trip/transportmode.md) hint indicating the type of transport being used, if known. |
| callback          | A [`StartTripCallback`](trip/starttripcallback.md) to handle trip start success and failure.           |

### `stop()`

{% hint style="warning" %}
This method is deprecated. Use [`disableDetections()`](sentiance.md.md#disabledetections) instead.
{% endhint %}

> ```java
> void stop()
> ```
>
> Stops the SDK detections.

### `stopTrip()`

> ```java
> PendingOperation<StopTripResult, StopTripError> stopTrip()
> ```
>
> Stops the currently ongoing external trip (i.e one that was started by calling [`startTrip(Map, TransportMode)`](sentiance.md.md#starttrip-map-transportmode).
>
> \
> Returns [`StopTripResult`](stoptripresult.md) upon success or [`StopTripError`](stoptriperror/) upon failure via [PendingOperation](pendingoperation/).

### `stopTrip(StopTripCallback)`

{% hint style="warning" %}
This method is deprecated. Use [`stopTrip()`](sentiance.md.md#stoptrip) instead.
{% endhint %}

> ```java
> void stopTrip(@Nullable StopTripCallback callback)
> ```
>
> Stops the currently ongoing external trip (started by calling [`starTrip()`](sentiance.md.md#starttrip-map-transportmode-starttripcallback)).
>
> To learn more about external trips, see [controlled detections](../../appendix/controlled-detections/).

| Parameters |                                                                                           |
| ---------- | ----------------------------------------------------------------------------------------- |
| callback   | A [`StopTripCallback`](trip/stoptripcallback.md) to handle trip stop success and failure. |

### `submitDetections()`

> ```java
> PendingOperation<SubmitDetectionsResult, SubmitDetectionsError> submitDetections()
> ```
>
> Submits any pending SDK detection to the Sentiance API.
>
> This method will bypass any network quota limitation set for the SDK. A typical use case would be when the enclosing app determines (via [`getDiskQuotaUsage()`](sentiance.md.md#getdiskquotausage) or [`SdkStatus#diskQuotaStatus)`](sdkstatus/#diskquotastatus) that there are too many detections on disk that have not yet been submitted.
>
> Returns [`SubmitDetectionsResult`](submitdetectionsresult.md) upon success or [`SubmitDetectionsError`](submitdetectionserror/) upon failure via [PendingOperation](pendingoperation/).

### `submitDetections(SubmitDetectionsCallback)`

{% hint style="warning" %}
This method is deprecated. Use `submitDetections()` instead.
{% endhint %}

> ```java
> void submitDetections(@Nullable SubmitDetectionsCallback callback)
> ```
>
> Submits the detections to the Sentiance API. This will bypass any network quota limitation.
>
> A typical use case of this method would be when the enclosing app determines (via [`getDiskQuotaUsage()`](sentiance.md.md#getdiskquotausage) or [`SdkStatus.diskQuotaStatus`](sdkstatus/#diskquotastatus)) that there are too many detections on disk that have not yet been submitted.

| Parameters |                                                                                      |
| ---------- | ------------------------------------------------------------------------------------ |
| callback   | A [`SubmitDetectionsCallback`](submitdetectionscallback.md) invoked with the result. |

### `updateSdkNotification()`

> ```java
> void updateSdkNotification(Notification notification)
> ```
>
> Replaces the notification set via [`SentianceOptions.Builder#setNotification(Notification, int)`](sentianceoptions/sentianceoptions.builder.md#setnotification). After calling this method, any service notification shown by the SDK will be updated.
>
>
>
> Note that the notification update done by this method is valid only during the app's lifetime. After the app restarts, the SDK will default back to the notification set during SDK initialization (or a default one if nothing was specified).

| Parameters   |                                                                                                                                          |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| notification | A [`Notification`](https://developer.android.com/reference/android/app/Notification) used by the SDK when starting a foreground service. |
