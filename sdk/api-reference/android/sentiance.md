# Sentiance

The Sentiance class is the main entry point for interacting with the SDK. This class is a singleton, therefore you can obtain an instance as follows:

```java
Sentiance sentianceSDK = Sentiance.getInstance(context);
```

## Sentiance API

|  |  |
| :--- | :--- |
| void  | [addUserMetadataField](sentiance.md#addusermetadatafield) \(String label, String value\) |
| void | [addUserMetadataFields](sentiance.md#addusermetadatafields) \(Map&lt;String, String&gt; metadata\) |
| boolean | [addTripMetadata](sentiance.md#addtripmetadata) \(Map&lt;String, String&gt; metadata\) |
| void | [disableBatteryOptimization](sentiance.md#disablebatteryoptimization) \(\) |
| long  | [getDiskQuotaLimit](sentiance.md#getdiskquotalimit) \(\) |
| long  | [getDiskQuotaUsage](sentiance.md#getdiskquotausage) \(\) |
| [InitState](initstate.md)  | [getInitState](sentiance.md#getinitstate) \(\) |
| [Sentiance](sentiance.md) | [getInstance](sentiance.md#getinstance) \([Context](https://developer.android.com/reference/android/content/Context) context\) |
| long  | [getMobileQuotaLimit](sentiance.md#getmobilequotalimit) \(\) |
| long  | [getMobileQuotaUsage](sentiance.md#getmobilequotausage) \(\) |
| [SdkStatus](sdkstatus/)  | [getSdkStatus](sentiance.md#getsdkstatus) \(\) |
| void  | [getUserAccessToken](sentiance.md#getuseraccesstoken) \([TokenResultCallback](tokenresultcallback.md) callback\) |
| [UserActivity](useractivity.md) | [getUserActivity](sentiance.md#getuseractivity) \(\) |
| String  | [getUserId](sentiance.md#getuserid) \(\) |
| String  | [getVersion](sentiance.md#getversion) \(\) |
| long  | [getWiFiQuotaLimit](sentiance.md#getwifiquotalimit) \(\) |
| long  | [getWiFiQuotaUsage](sentiance.md#getwifiquotausage) \(\) |
| void | [init](sentiance.md#init) \([SdkConfig](sdkconfig/) sdkConfig, [OnInitCallback](oninitcallback/) initCallback\) |
| boolean  | [isTripOngoing](sentiance.md#istripongoing) \([TripType](trip/triptype.md) tripType\) |
| void  | [removeUserMetadataField](sentiance.md#removeusermetadatafield) \(String label\) |
| void | [reset](sentiance.md#reset) \([ResetCallback](resetcallback/) callback\) |
| void  | [setCrashCallback](sentiance.md#setcrashcallback) \(@Nullable [CrashCallback](crashdetection/crashcallback.md) callback\) |
| void  | [setTripTimeoutListener](sentiance.md#settriptimeoutlistener) \(@Nullable [TripTimeoutListener](trip/triptimeoutlistener.md) listener\) |
| void | [setUserActivityListener](sentiance.md#setuseractivitylistener) \(@Nullable [UserActivityListener](useractivitylistener.md) listener\) |
| void  | [start](sentiance.md#start) \([OnStartFinishedHandler](onstartfinishedhandler.md) handler\) |
| void | [start](sentiance.md#start-1) \([Date](https://developer.android.com/reference/java/util/Date) stopDate, [OnStartFinishedHandler](onstartfinishedhandler.md) handler\) |
| void  | [startTrip](sentiance.md#starttrip) \(final @Nullable Map&lt;String, String&gt; metadata, final @Nullable [TransportMode](trip/transportmode.md) transportModeHint, @Nullable [StartTripCallback](trip/starttripcallback.md) callback\) |
| void  | [stop](sentiance.md#stop) \(\) |
| void  | [stopTrip](sentiance.md#stoptrip) \(@Nullable [StopTripCallback](trip/stoptripcallback.md) callback\) |
| void  | [submitDetections](sentiance.md#submitdetections) \(@Nullable [SubmitDetectionsCallback](submitdetectionscallback.md) callback\) |
| void | [updateSdkNotification](sentiance.md#updatesdknotification) \([Notification](https://developer.android.com/reference/android/app/Notification) notification\) |



### `addUserMetadataField()`

> ```java
> void addUserMetadataField(String label, String value)
> ```
>
> Adds a user specific metadata field.
>
> | Parameters |  |
> | :--- | :--- |
> | label | Metadata label to add. |
> | value | Metadata value. |

### `addUserMetadataFields()`

> ```java
> void addUserMetadataFields(Map<String, String> metadata)
> ```
>
> Adds multiple user specific metadata fields.
>
> | Parameters |  |
> | :--- | :--- |
> | metadata | The metadata fields. |

### `addTripMetadata()`

> ```java
> boolean addTripMetadata(Map<String, String> metadata)
> ```
>
> Adds metadata while an external trip is ongoing. This method can be called multiple times during a trip.
>
> This method returns false if there is no ongoing external trip or `null` metadata is passed.
>
> | Parameters |  |
> | :--- | :--- |
> | metadata | A map of metadata pertaining to the ongoing trip, which will be saved along with the trip data. |

### `disableBatteryOptimization()`

> ```java
> void disableBatteryOptimization()
> ```
>
> Generates a system dialog asking the user to allow disabling battery optimization for the app.
>
> Learn more about disabling battery optimization [here](../../appendix/android/android-battery-optimization.md).

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
> Returns an instance of the [`Sentiance`](sentiance.md) class.
>
> This method will call [`Context.getApplicationContext()`](https://developer.android.com/reference/android/content/Context.html#getApplicationContext%28%29) on the passed context to prevent memory leaks when passing an Activity context.
>
> | Parameters |  |
> | :--- | :--- |
> | context | A [`Context`](https://developer.android.com/reference/android/content/Context) object. |

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

> ```java
> void getUserAccessToken(TokenResultCallback callback)
> ```
>
> Returns the user's API access token as a [`Token`](token.md) object via the specified callback.
>
> For more information regarding failure, see [`TokenResultCallback.onFailure()`](tokenresultcallback.md#onfailure).
>
> | Parameters |  |
> | :--- | :--- |
> | callback | A callback to handle the token result. Note that the SDK holds a [weak reference](https://developer.android.com/reference/java/lang/ref/WeakReference) to this callback in order to prevent component leaks. Make sure you have a strong reference to it in order to guarantee its execution. |

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

### `init()`

> ```java
> void init(SdkConfig sdkConfig, final OnInitCallback initCallback)
> ```
>
> Initializes the Sentiance Sdk. 
>
> This method constructs internal SDK components and prepares the SDK for handling app and system requests. If a Sentiance user does not yet exist on the device, this method triggers user creation on the Sentiance Platform, which requires internet connectivity.
>
> During the lifetime of the app process, calling this method again after a successful initialization is not allowed. Doing so is regarded as an error and therefore throws an [`SdkException`](sdkexception.md) at runtime. To reinitialize the SDK with a different configuration or to create a new Sentiance user, first call `reset(ResetCallback)`.
>
> All methods in this class \(except this method, [`reset(ResetCallback)`](sentiance.md#reset), [`getInitState()`](sentiance.md#getinitstate) and [`getVersion()`](sentiance.md#getversion)\) will throw an [`SdkException`](sdkexception.md) when called before initialization has completed.
>
> | Parameters |  |
> | :--- | :--- |
> | sdkConfig | An [`SdkConfig`](sdkconfig/) representing the SDK configuration. |
> | initCallback | An [`OnInitCallback`](oninitcallback/) to handle the initialization of the Sdk. |

### `isTripOngoing()`

> ```java
> boolean isTripOngoing(TripType tripType)
> ```
>
> Indicates whether a trip is in progress.
>
> | Parameters |  |
> | :--- | :--- |
> | tripType | A [`TripType`](trip/triptype.md) enum indicating the type of trip the caller is interested in. |

### `removeUserMetadataField()`

> ```java
> void removeUserMetadataField(String label)
> ```
>
> Removes a user specific metadata field.
>
> | Parameters |  |
> | :--- | :--- |
> | label | Metadata to remove. |

### `reset()`

> ```java
> void reset(@Nullable ResetCallback callback)
> ```
>
> Resets the Sentiance Sdk.
>
> Calling this method results in stopping of all SDK operations and deleting all SDK user data from the device. Additionally, the SDK will be uninitialized, allowing reinitialization and new Sentiance user creation.
>
> The reset operation may take a while, in which case the SDK's initialization state will be set to `InitState.RESETTING` until it's complete. Calling any other SDK method during this time will either be ignored or return a default value. While resetting, make sure your app is in the foreground to prevent process termination \(i.e. an activity is open, or a foreground service is running\).
>
> Note that calling this method during intermediate initialization states \(i.e. `INIT_IN_PROGRESS` and `RESETTING`\) will fail.
>
> | Parameters |  |
> | :--- | :--- |
> | callback | A [`ResetCallback`](resetcallback/) to handle the reset completion. |

### `setCrashCallback()`

> ```java
> void setCrashCallback(@Nullable CrashCallback callback)
> ```
>
> Sets a callback that is invoked when a vehicle crash is detected.
>
> | Parameters |  |
> | :--- | :--- |
> | callback | A [`CrashCallback`](crashdetection/crashcallback.md) object to receive crash time and location. |

### `setTripTimeoutListener()`

> ```java
> void setTripTimeoutListener(@Nullable TripTimeoutListener listener)
> ```
>
> Sets a listener that is invoked when a trip times out. This method is relevant only when triggered trips are enabled via [`setTriggeredTripsEnabled(boolean)`](sdkconfig/sdkconfig-builder.md#settriggeredtripsenabled) on the [`SdkConfig.Builder`](sdkconfig/sdkconfig-builder.md) object. Trips do not time out otherwise.
>
> To learn more about trip timeouts, see [controlled detections](../../appendix/controlled-detections/controlled-trips-only.md).
>
> | Parameters |  |
> | :--- | :--- |
> | listener | A [`TripTimeoutListener`](trip/triptimeoutlistener.md) to handle trip timeouts, or null to remove the previous listener. |

### `setUserActivityListener()`

> ```java
> void setUserActivityListener(@Nullable UserActivityListener listener)
> ```
>
> Sets a listener that is invoked when a new user activity is detected. After calling this method, the current user activity will be immediately delivered to the listener.
>
> | Parameters |  |
> | :--- | :--- |
> | listener | A [`UserActivityListener`](useractivitylistener.md) to handle [`UserActivity`](useractivity.md) changes, or null to remove the previous listener. |

### `start()`

> ```java
> void start(OnStartFinishedHandler handler)
> ```
>
> Starts the SDK detections.
>
> When this process has finished, [`OnStartFinishedHandler.onStartFinished(SdkStatus)`](onstartfinishedhandler.md#onstartfinished) will be called. This does not necessarily mean that the SDK is actually performing detections. You may use the [`SdkStatus`](sdkstatus/) passed to the [`onStartFinished(SdkStatus)`](onstartfinishedhandler.md#onstartfinished) method to determine why.
>
> To automatically stop detections, call the [`start(Date, OnStartFinishedHandler)`](sentiance.md#start-1) method instead. You do not need to call [`stop()`](sentiance.md#stop) beforehand as all start calls override each other.
>
> | Parameters |  |
> | :--- | :--- |
> | handler | A [`OnStartFinishedHandler`](trip/triptimeoutlistener.md) used to notify that the SDK start has finished. Note that the SDK holds a [weak reference](https://developer.android.com/reference/java/lang/ref/WeakReference) to this handler to in order to prevent component leaks. Make sure you have a strong reference to it in order to guarantee its execution. |

### `start()`

> ```java
> void start(Date stopDate, OnStartFinishedHandler handler)
> ```
>
> Starts the SDK detections.
>
> This method has the same behaviour as [`start(OnStartFinishedHandler)`](sentiance.md#start) except an absolute date is passed to automatically stop the SDK some time in the future. A typical use-case is when the app provides a free trial period for its users after which the SDK should stop running.
>
> To cancel the auto-stop functionality, you can call this method with a null stopDate or just call [`start(OnStartFinishedHandler)`](sentiance.md#start). You do not need to call [`stop()`](sentiance.md#stop) beforehand as all start calls override each other.
>
> | Parameters |  |
> | :--- | :--- |
> | stopDate | An absolute date at which the SDK is stopped. If the date is in the past, the SDK will stop immediately. |
> | handler | A [`OnStartFinishedHandler`](trip/triptimeoutlistener.md) used to notify that the SDK start has finished. Note that the SDK holds a [weak reference](https://developer.android.com/reference/java/lang/ref/WeakReference) to this handler to in order to prevent component leaks. Make sure you have a strong reference to it in order to guarantee its execution. |

### `startTrip()`

> ```java
> void startTrip(@Nullable Map<String, String> metadata, 
>                @Nullable TransportMode transportModeHint, 
>                @Nullable StartTripCallback callback)
> ```
>
> Starts an external trip.
>
> To learn more about external trips, see [controlled detections](../../appendix/controlled-detections/).
>
> | Parameters |  |
> | :--- | :--- |
> | metadata | A map of metadata pertaining to the newly started trip, which will be saved along with the trip data. |
> | transportModeHint | A [`TransportMode`](trip/transportmode.md) hint indicating the type of transport being used, if known. |
> | callback | A [`StartTripCallback`](trip/starttripcallback.md) to handle trip start success and failure. |

### `stop()`

> ```java
> void stop()
> ```
>
> Stops the SDK detections.

### `stopTrip()`

> ```java
> void stopTrip(@Nullable StopTripCallback callback)
> ```
>
> Stops the currently ongoing external trip \(started by calling [`starTrip()`](sentiance.md#starttrip)\).
>
> To learn more about external trips, see [controlled detections](../../appendix/controlled-detections/).
>
> | Parameters |  |
> | :--- | :--- |
> | callback | A [`StopTripCallback`](trip/stoptripcallback.md) to handle trip stop success and failure. |

### `submitDetections()`

> ```java
> void submitDetections(@Nullable SubmitDetectionsCallback callback)
> ```
>
> Submits the detections to the Sentiance API. This will bypass any network quota limitation.
>
>  A typical use case of this method would be when the enclosing app determines \(via [`getDiskQuotaUsage()`](sentiance.md#getdiskquotausage) or [`SdkStatus.diskQuotaStatus`](sdkstatus/#diskquotastatus)\) that there are too many detections on disk that have not yet been submitted.
>
> | Parameters |  |
> | :--- | :--- |
> | callback | A [`SubmitDetectionsCallback`](submitdetectionscallback.md) invoked with the result. |

### `updateSdkNotification()`

> ```java
> void updateSdkNotification(Notification notification)
> ```
>
> Replaces the notification set in [`SdkConfig.Builder`](sdkconfig/sdkconfig-builder.md). After calling this method, any notification shown by the SDK will be updated.
>
>  Note that this change is valid only during the process's lifetime. After the app process restarts, the SDK will default back to the notification set in [`SdkConfig.Builder`](sdkconfig/sdkconfig-builder.md).
>
> | Parameters |  |
> | :--- | :--- |
> | notification | A [`Notification`](https://developer.android.com/reference/android/app/Notification) used by the SDK when starting a foreground service. |

