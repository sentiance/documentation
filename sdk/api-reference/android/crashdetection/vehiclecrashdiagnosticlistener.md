# VehicleCrashDiagnosticListener

This interface is used in combination with  [`setVehicleCrashDiagnosticListener(VehicleCrashDiagnosticListener)`](../crashdetectionapi.md#setvehiclecrashdiagnosticlistener).

## VehicleCrashDiagnosticListener API

### `onNewDiagnostic()`

> ```java
> void onNewDiagnostic(@NonNull VehicleCrashDiagnostic diagnostic);
> ```
>
> Called when new vehicle crash diagnostic data is available.

| diagnostic | A [VehicleCrashDiagnostic](vehiclecrashdiagnostic.md) object containing diagnostic data pertaining to an ongoing vehicle crash detection. |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------- |

