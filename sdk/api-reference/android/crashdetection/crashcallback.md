# CrashCallback

This interface is used with [`setCrashCallback(CrashCallback)`](../sentiance.md#setcrashcallback).

## CrashCallback API

|  |  |
| :--- | :--- |
| void | [onCrash](crashcallback.md#oncrash) \(long time, @Nullable [Location](https://developer.android.com/reference/android/location/Location) lastKnownLocation\) |



### `onCrash()`

> ```java
> void onCrash(long time, @Nullable Location lastKnownLocation)
> ```
>
> Called when a vehicle crash is detected during a trip. 
>
> | Parameters |  |
> | :--- | :--- |
> | time | The UTC time of the detected crash in milliseconds. |
> | lastKnownLocation | A [Location](https://developer.android.com/reference/android/location/Location) object indicating the last known location of the device when the crash was detected. |

