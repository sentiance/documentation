# VehicleCrashListener

This interface is used with [`setVehicleCrashListener(VehicleCrashListener)`](../sentiance.md#setvehiclecrashlistener).

## VehicleCrashListener API

|  |  |
| :--- | :--- |
| void | onVehicleCrash \([VehicleCrashEvent](vehiclecrashevent.md) crashEvent\) |



### `onVehicleCrash()`

> ```java
> void onVehicleCrash(VehicleCrashEvent crashEvent)
> ```
>
> Called when a vehicle crash is detected during a trip. Use this method to receive details about the crash.
>
> | Parameters |  |
> | :--- | :--- |
> | crashEvent | A [`VehicleCrashEvent`](vehiclecrashevent.md) object that contains crash metrics. |
