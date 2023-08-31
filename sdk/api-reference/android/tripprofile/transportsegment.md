# TransportSegment

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v4.21.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

A segment is a section of the trip where the user was using the same [`VehicleMode`](vehiclemode.md) for the specified time range. When the mode is `VehicleMode.VEHICLE`, certain transport metrics can be accessed using the methods below.

## TransportSegment API

### `getAverageSpeed()`

> ```java
> public Double getAverageSpeed()
> ```
>
> Returns the average speed travelled in m/s.

### `getDistance()`

> ```java
> public VehicleMode getDistance()
> ```
>
> Returns the cumulative distance covered in this segment in meters.

### `getEndTime()`

> ```java
> public long getEndTime()
> ```
>
> Returns the segment's end time, in UTC milliseconds since January 1, 1970.

### `getHardEvents()`

> ```java
> public List<HardEvent> getHardEvents()
> ```
>
> Returns a list of [`HardEvent`](hardevent.md) objects for all the times the device has experienced an unusual amount of force while in [`VehicleMode.VEHICLE`](vehiclemode.md). Otherwise returns null.

### `getPercentOfTimeSpeeding()`

> ```java
> public Integer getPercentOfTimeSpeeding()
> ```
>
> Returns the percent of time the user was speeding.

### `getStartTime()`

> ```java
> public long getStartTime()
> ```
>
> Returns the segment's start time, in UTC milliseconds since January 1, 1970.

### `getTopSpeed()`

> ```java
> public Double getTopSpeed()
> ```
>
> Returns the top speed travelled in m/s.

### `getVehicleMode()`

> ```java
> public VehicleMode getVehicleMode()
> ```
>
> Returns the vehicle mode of this segment. See [`VehicleMode`](vehiclemode.md) for more details.
