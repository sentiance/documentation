# CrashCallback

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
This interface is deprecated. Use [`VehicleCrashListener`](vehiclecrashevent.md) instead. See [`setVehicleCrashListener(VehicleCrashListener)`](../sentiance.md#setvehiclecrashlistener).
{% endhint %}

This interface is used with [`setCrashCallback(CrashCallback)`](../sentiance.md#setcrashcallback).

## CrashCallback API

### `onCrash()`

> ```java
> void onCrash(long time, @Nullable Location lastKnownLocation)
> ```
>
> Called when a vehicle crash is detected during a trip.&#x20;

| Parameters        |                                                                                                                                                                      |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| time              | The UTC time of the detected crash in milliseconds.                                                                                                                  |
| lastKnownLocation | A [Location](https://developer.android.com/reference/android/location/Location) object indicating the last known location of the device when the crash was detected. |
