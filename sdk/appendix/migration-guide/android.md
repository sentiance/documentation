# Android

## Migrating from 3.x to 4.x

{% hint style="info" %}
This update brings Android Oreo compatibility. You will now be able to target API level 28.
{% endhint %}

### SDK Initialization

Initializing the SDK is done by calling the [`init()`](../../api-reference/android/sentiance.md#init) method and passing an [`SdkConfig`](../../api-reference/android/sdkconfig/) object.[`SdkConfig.Builder`](../../api-reference/android/sdkconfig/sdkconfig-builder.md) now expects a notification as the 3rd parameter. `enableForeground(notification)` is no longer available for this purpose. The SDK will show a notification depending on the OS version, targeted API level, and remote app configuration.

### SDK Control

The `stopAfter(seconds)` method is no longer available.

### User Metadata

User metadata methods no longer accept `MetadataCallback` as a 3rd parameter. Adding and removing metadata is now done asynchronously via the payload submission system.

### External Events

Registering external events is no longer available.

### Trip Control

#### Starting and Stopping Trips

\`\`[`startTrip()`](../../api-reference/android/sentiance.md#starttrip) and [`stopTrip()`](../../api-reference/android/sentiance.md#starttrip) methods now require [`StartTripCallback`](../../api-reference/android/trip/starttripcallback.md) and [`StopTripCallback`](../../api-reference/android/trip/stoptripcallback.md) parameters respectively.

#### Trip Details

The SDK no longer returns a `Trip` object when a trip is stopped. The [`onTripTimeout()`](../../api-reference/android/trip/triptimeoutlistener.md#ontriptimeout)method of [`TripTimeoutListener`](../../api-reference/android/trip/triptimeoutlistener.md) no longer returns a `Trip` object. Similarly, the `onTripStopped()` method of [`StopTripCallback`](../../api-reference/android/trip/stoptripcallback.md) no longer exists. This interface now provides an [`onSuccess()`](../../api-reference/android/trip/stoptripcallback.md#onsuccess) and [`onFailure(sdkStatus)`](../../api-reference/android/trip/stoptripcallback.md#onfailure) methods.

#### Checking Ongoing Trips

The [`isTripOngoing()`](../../api-reference/android/sentiance.md#istripongoing) method now expects a parameter of type [`TripType`](../../api-reference/android/trip/triptype.md).

### Callbacks

All callback and listener methods are now executed on the application's main thread. If you perform any long running or network operations directly in the callbacks, please take care to move them to a background thread instead.

### Other

`getWiFiLastSeenTimestamp()` is no longer available.

The [`CrashCallback`](../../api-reference/android/crashdetection/crashcallback.md)'s Location parameter is now `@Nullable`.

