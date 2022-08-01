# CrashDetectionApi

## CrashDetectionApi

| void    | [invokeDummyVehicleCrash](crashdetectionapi.md#invokedummyvehiclecrash)()                     |
| ------- | --------------------------------------------------------------------------------------------- |
| boolean | [isVehicleCrashDetectionSupported](crashdetectionapi.md#isvehiclecrashdetectionsupported)()   |
| void    | [setVehicleCrashListener(VehicleCrashListener)](crashdetectionapi.md#setvehiclecrashlistener) |



### `invokeDummyVehicleCrash()`

> ```java
> void invokeDummyVehicleCrash()
> ```
>
> Invokes a dummy vehicle crash event. Use this method to test your vehicle crash detection integration.
>
>
>
> Calling this method will invoke the [VehicleCrashListener#onVehicleCrash(VehicleCrashEvent) ](crashdetection/vehiclecrashlistener.md#onvehiclecrash)method of your [VehicleCrashListener](crashdetection/vehiclecrashlistener.md) implementation, set via [setVehicleCrashListener(VehicleCrashListener)](crashdetectionapi.md#setvehiclecrashlistener).
>
> Note that this method is intended for testing your integration, and will only run on debug versions of your app (i.e. when the `android:debuggable` manifest flag is set to `true`).

### `isVehicleCrashDetectionSupported()`

> ```java
> boolean isVehicleCrashDetectionSupported()
> ```
>
> Returns whether vehicle crash detection is supported on the device.
>
> The result depends on multiple criteria, such as if vehicle crash detection is enabled for your app, and if the necessary sensors are present on the device.

### `setVehicleCrashListener()`

> ```java
> void setVehicleCrashListener(@Nullable VehicleCrashListener listener)
> ```
>
> Sets a listener that is invoked when a vehicle crash is detected.

| Parameters |                                                                                                                                                          |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| listener   | A [`VehicleCrashListener`](crashdetection/vehiclecrashlistener.md) to receive details about the crash. Set `null` to remove the previously set listener. |

``
