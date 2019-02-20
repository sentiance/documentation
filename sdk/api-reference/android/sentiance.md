# Sentiance

The Sentiance class is the main entry point for interacting with the SDK. This class is a singleton, therefore you can obtain an instance as follows:

```java
Sentiance sentianceSDK = Sentiance.getInstance(context);
```

## Sentiance API

|  |  |
| :--- | :--- |
| void  | [addUserMetadataField](sentiance.md#addusermetadatafield) \(String label, String value\) |
| void | [addUserMetadataFields](sentiance.md#addusermetadatafields) \(Map&lt; String, String &gt; metadata\) |
| void | [disableBatteryOptimization](sentiance.md#disablebatteryoptimization) \(\) |
| long  | [getDiskQuotaLimit](sentiance.md#getdiskquotalimit) \(\) |
| long  | [getDiskQuotaUsage](sentiance.md#getdiskquotausage) \(\) |
| [InitState](initstate.md)  | [getInitState](sentiance.md#getinitstate) \(\) |
| [Sentiance](sentiance.md) | getInstance \([Context](https://developer.android.com/reference/android/content/Context) context\) |
| long  | [getMobileQuotaLimit](sentiance.md#getmobilequotalimit) \(\) |
| long  | [getMobileQuotaUsage](sentiance.md#getmobilequotausage) \(\) |
| [SdkStatus](sdkstatus/)  | [getSdkStatus](sentiance.md#getsdkstatus) \(\) |
| void  | [getUserAccessToken](sentiance.md#getuseraccesstoken) \([TokenResultCallback](tokenresultcallback.md) callback\) |
| String  | [getUserId](sentiance.md#getuserid) \(\) |
| String  | [getVersion](sentiance.md#getversion) \(\) |
| long  | [getWiFiQuotaLimit](sentiance.md#getwifiquotalimit) \(\) |
| long  | [getWiFiQuotaUsage](sentiance.md#getwifiquotausage) \(\) |
| void | [init](sentiance.md#init) \([SdkConfig](sdkconfig/) sdkConfig, final [OnInitCallback](oninitcallback/) initCallback\) |
| boolean  | [isTripOngoing](sentiance.md#istripongoing) \([TripType](trip/triptype.md) tripType\) |
| void  | [removeUserMetadataField](sentiance.md#removeusermetadatafield) \(String label\) |
| void  | [setCrashCallback](sentiance.md#setcrashcallback) \(@Nullable final [CrashCallback](crashdetection/crashcallback.md) callback\) |
| void  | [setTripTimeoutListener](sentiance.md#settriptimeoutlistener) \(final [TripTimeoutListener](trip/triptimeoutlistener.md) listener\) |
| void  | [start](sentiance.md#start) \([OnStartFinishedHandler](onstartfinishedhandler.md) handler\) |
| void  | [startTrip](sentiance.md#starttrip) \(final @Nullable Map&lt;String, String&gt; metadata, final @Nullable [TransportMode](trip/transportmode.md) transportModeHint, @Nullable [StartTripCallback](trip/starttripcallback.md) callback\) |
| void  | [stop](sentiance.md#stop) \(\) |
| void  | [stopTrip](sentiance.md#stoptrip) \(@Nullable [StopTripCallback](trip/stoptripcallback.md) callback\) |
| void  | [submitDetections](sentiance.md#submitdetections) \(@Nullable [SubmitDetectionsCallback](submitdetectionscallback.md) callback\) |



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
> | callback | A callback to handle the token result. |

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
> Initializes the Sentiance Sdk. This method may only be called once, and will throw an [`SdkException`](sdkexception.md) if called multiple times.
>
> All methods in this interface \(except this method, [`getInitState()`](sentiance.md#getinitstate) and [`getVersion()`](sentiance.md#getversion)\) will throw an [`SdkException`](sdkexception.md) when called before initialization has completed.
>
> | Parameters |  |
> | :--- | :--- |
> | sdkConfig | An [`SdkConfig`](sdkconfig/) representing the SDK configuration. |
> | initCallback | An [`OnInitCallback`](oninitcallback/) object to handle the initialization of the Sdk. |

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
> | listener | A [`TripTimeoutListener`](trip/triptimeoutlistener.md) to handle trip timeouts. |

### `start()`

> ```java
> void start(OnStartFinishedHandler handler)
> ```
>
> Starts the SDK detections.
>
> When this process has finished, [`OnStartFinishedHandler.onStartFinished(SdkStatus)`](onstartfinishedhandler.md#onstartfinished) will be called. This does not necessarily mean that the SDK is actually performing detections. You may use the [`SdkStatus`](sdkstatus/) passed to the [`onStartFinished(SdkStatus)`](onstartfinishedhandler.md#onstartfinished) method to determine why.
>
> | Parameters |  |
> | :--- | :--- |
> | listener | A [`TripTimeoutListener`](trip/triptimeoutlistener.md) to handle trip timeouts. |

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
