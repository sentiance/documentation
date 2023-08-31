# VehicleCrashListener

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`setVehicleCrashListener(VehicleCrashListener)`](../sentiance.md#setvehiclecrashlistener).

## VehicleCrashListener API

### `onVehicleCrash()`

> ```java
> void onVehicleCrash(VehicleCrashEvent crashEvent)
> ```
>
> Called when a vehicle crash is detected during a trip. Use this method to receive details about the crash.

| Parameters |                                                                                   |
| ---------- | --------------------------------------------------------------------------------- |
| crashEvent | A [`VehicleCrashEvent`](vehiclecrashevent.md) object that contains crash metrics. |
